# CLIPIN — Video Clipping, YouTube Clipping & Design Memory Extraction

**Document ID:** CLIPIN-MEMORY-EXTRACTION-001  
**Version:** 1.0  
**Prepared:** 14 October 2026  
**Status:** Working extraction from retrievable conversation-memory artifacts  
**Scope:** Video clipping, YouTube clipping, short-form content generation, CLIPIN product design, AI prompt architecture, APIs, integrations, UI components, and implementation guidance.

> **Completeness and evidence note:** This document consolidates the relevant material found in the retrievable CLIPIN platform architecture/design specification and CLIPIN AI implementation transcript, along with the directly related design and prompt-compiler conversation. It preserves the design decisions, proposed features, interfaces, data models, implementation snippets' intent, dependencies, and unresolved issues. It does not claim that every historical conversation in the entire account has been inspected. A specification or pasted code proposal is not proof that the code was committed, deployed, tested, or remains current. Historical provider names, platform limits, pricing, quotas, and API examples are retained as *claims in the prior material*, not independently verified current facts.

---

# 1. Executive synthesis

## 1.1 What the project is

**CLIPIN** is described as a web and mobile-first creator platform that turns long-form video content into short, platform-ready clips. The proposed system combines:

1. AI-assisted extraction of promising moments from video transcripts.
2. YouTube, TikTok, Instagram, and Google Drive URL/context inputs.
3. Clip cards containing titles, quote previews, durations, timestamps, and quality/viral-potential scores.
4. Manual clip boundaries as well as whole-video options.
5. Platform-aware exports and aspect-ratio formatting, including vertical 9:16 outputs for TikTok, Instagram Reels, and YouTube Shorts.
6. Video ideation, hooks, scripting, script outlining, script rewriting, titles, descriptions, chapters, tags/hashtags, subtitle cleanup, and clip-quality review.
7. Scheduling, publishing, and content storage workflows.
8. Monetisation estimates, earned media value (EMV), and brand-deal estimation.
9. Creator training and a method for learning how to identify high-value clipping moments.
10. A versioned AI prompt registry, OpenRouter integration, structured output validation, retries, usage tracking, and a safe crawling/research utility.

## 1.2 Product proposition recorded in the source

The onboarding language includes:

- **“One Video. Infinite Clips.”** Upload once; turn long-form content into daily clips.
- **“Every Platform, Every Day.”** Format and schedule for TikTok, Instagram Reels, and YouTube Shorts from one workflow.
- **“Flexible to Your Style.”** Choose AI auto-clipping or define moments manually.

The tool experience combines a guided clipping workflow with a wider set of creator utilities, rather than being only a YouTube clip cutter.

## 1.3 Names, code and source artifacts found

- Product name used in the recovered specification: **CLIPIN**.
- Repository referred to in implementation transcript: `Logonotobscurity/clip-creator-studio`.
- Design specification file recovered from Library: `Pasted markdown(2).md`, titled **CLIPIN Platform — Design Architecture & API Specification**, v1.0, dated in the recovered system as 8 August 2026.
- AI implementation transcript recovered from Library: `Pasted text(20260809-065238).txt`, dated 9 August 2026.
- AI architecture includes `src/lib/ai-gateway.server.ts`, `src/lib/ai/prompt-registry.ts`, task executor, crawl engine, AI service facade, environment template, and AI implementation guide as proposed/recorded changes.
- Prior interaction transcript includes approval-like messages (“accepted the action”, “proceed”), but **repository state was not inspected here**; therefore these messages cannot establish that each change reached the default branch or passed CI.

---

# 2. Core user journeys and functional scope

## 2.1 Main user flow

The recovered flow is:

`App Launch → Onboarding → Authentication → Tool Hub → Select Tool → Enter URL/Topic + Context → AI Processing → Results → Detail/Edit → Export/Share/Schedule → History/Analytics`

For clipping specifically:

`YouTube/TikTok/Instagram/Google Drive URL or supported input → Video/transcript analysis → Candidate moments → Clip results → Select a result → Choose whole video or manual cut → Set start/end time → Export/share/schedule`

The source indicates a separate AI/creative branch from the Tool Hub:

`Topic + platform + audience → Ideas / hooks / script / titles / descriptions / chapters / tags → Edit/copy/export`

## 2.2 Core tool families in the Hub

### Repurpose
- Short Clip Maker → `/app/clipmaker`
- Clip from URL → `/app/clipmaker?mode=url`

### Ideate
- Unlimited Video Ideas → `/app/ideate`
- Hook Generator → `/app/hooks`

### Scripting
- Script Writer → `/app/script/write`
- Script Outline → `/app/script/outline`
- Rewrite from Video → `/app/script/rewrite`

### Upload & Optimise
- Video Title → `/app/optimise/title`
- Video Description → `/app/optimise/description`
- Video Chapters → `/app/optimise/chapters`
- Video Tags → `/app/optimise/tags`

### Monetise
- Earnings Calculator → `/app/monetise`
- Brand Deal Estimator → `/app/deals`

### Schedule
- Publishing Hub → `/app/schedule`

### History
- Recent history shows up to three items on the Tool Hub.
- “View all” routes to `/app/history`.
- History records support types including `youtube`, `clip`, and `project`, together with title, date and recent action.

The specification also names `/app/analytics`, `/app/more`, and a five-item bottom navigation, although the corresponding detailed screen specifications were not fully enumerated in the source.

---

# 3. Video clipping: all extracted product behavior

## 3.1 Source inputs and context

The Short Clip Maker asks the user to paste a link. The text lists these supported input families:

- YouTube
- TikTok
- Instagram
- Google Drive

The URL entry is represented by a rounded `PillInput` with link icon, the placeholder **“Drop a video link”**, and an **AUTO** control.

Additional optional context fields:

- Inspiration channel or creator handle.
- Trending-in-country dropdown, with examples: Nigeria, United States, United Kingdom, Global.
- Additional context free-text area.
- The platform/niche/audience/context metadata used by AI task prompts.

The primary CTA is **“Generate Clips”**. States recorded:

- Empty input: placeholder remains and CTA is disabled/grey.
- URL entered: AUTO activates and CTA becomes active/blue.
- Loading: CTA displays a spinner and “Analysing video...”.
- Error: input border becomes red and error text appears below.

**Important technical distinction:** The UI describes accepting a video URL, but the clipping AI service accepts a transcript as input. A production implementation must explicitly implement and validate the bridge between URL/video source and transcript/media access. A URL pasted into the UI does not, by itself, imply that the video has been downloaded or transcribed.

## 3.2 AI moment extraction

The API specification defines `POST /api/ai/extract-clips`. Request fields:

```ts
interface ExtractClipsRequest {
  transcript: string;
  videoDurationSeconds: number;
  targetPlatforms: ('tiktok' | 'reels' | 'shorts')[];
  contextHint?: string;
  maxClips?: number;       // default 10 in this spec
  minDurationSec?: number; // default 15 in this spec
  maxDurationSec?: number; // default 60 in this spec
}
```

`contextHint` examples: comedy, education, gospel.

One response contract in the design/API document:

```ts
interface ClipMoment {
  index: number;
  clipTitle: string;              // short uppercase label, max 8 words
  quotePreview: string;           // first line of transcript segment
  startTimeSeconds: number;
  endTimeSeconds: number;
  durationSeconds: number;
  hookScore: number;              // AI-estimated, 0–100
  hookPattern:
    | 'shock_question'
    | 'roast_setup'
    | 'drama_tease'
    | 'community_call'
    | 'relatable'
    | 'value_reveal';
  recommendedPlatforms: string[];
  suggestedCaption?: string;
}
```

The associated system prompt says to identify moments likely to stop a viewer scrolling, particularly:

- Unexpected reveals.
- Emotional peaks.
- Punchlines.
- Quotable insights.

For each moment, it asks for a short uppercase title (maximum eight words), exact start/end timestamps, first-sentence quote preview, hook score from 0–100, hook-pattern label, and platform recommendations. Output is valid JSON only, without commentary.

## 3.3 A second candidate schema from the AI prompt registry

The later AI architecture transcript describes a versioned prompt task called `clip_candidates`, v1.0.0. It asks for 3–5 moments suitable for short-form content, generally 15–90 seconds, with a clear hook, compelling content and natural conclusion.

Its schema fields include:

- `momentNumber`
- `startTime` and `endTime` in `HH:MM:SS` format
- `duration` in seconds
- `hook`
- `transcript` containing the exact transcript excerpt
- `virality_score` from 0 to 100
- `reasoning`
- `suggested_platform`, constrained to TikTok, Instagram, or YouTube
- `summary` for the overall result

Input prompt variables include transcript, platform, creator niche, target audience and optional context. The prompt says to focus on emotional peaks, surprising reveals, or moments with clear value. It also instructs the model to consider platform, creator niche, audience demographics and trending hooks in the specified country.

## 3.4 Editorial quality criteria for a clip

The source material contains overlapping but useful criteria:

- Strong opening hook.
- Emotional peak, surprise, punchline, or actionable value.
- Clear subject or point.
- Natural conclusion rather than an arbitrary mid-sentence stop.
- Captions/quote preview faithful to the transcript.
- Suitable duration and platform fit.
- An estimated hook/virality/quality score.
- A rationale or explanation for the selected moment in the AI-layer version.
- Ability to revise the selected in/out points manually.

A generated “virality score” is an estimate, not a verified prediction. The system should label it as AI-estimated and later compare it with measured user outcomes if outcome data is available.

## 3.5 Manual cut versus whole video

The Clip Detail interaction is a BottomSheet titled **“Already have a clip in mind?”**. It shows:

- A “Use whole video” option.
- A “Cut manually” option.
- Start and end time fields.
- `HH:MM:SS` format hint.
- Primary CTA: **“CLIP MANUALLY”**.
- Optional upgrade copy: “Clip should be 10s to 60s, need more? Upgrade”.

The source puts the start/end inputs in a two-column light-grey inset block. Selected radio options expand to show associated content.

## 3.6 Clip results screen

Route: `/app/clipmaker/results`.

- Header: “Here are your Clips”.
- Summary: “We found [N] viral moments in your video.”
- A vertical list of numbered `ClipCard` entries.
- Floating action bar with sort, trim, and share-all actions.
- Tapping a clip card opens the clip detail sheet.
- Card displays an uppercase clip title, a quote excerpt clipped to three lines, duration metadata, and arrow CTA.
- Selection changes border to blue and background to pale blue.

## 3.7 Export, sharing, scheduling and status

The UI flow ends in export/schedule with a floating action bar supporting download, edit, and share. Platform posts are supposed to use a job queue with retries rather than direct synchronous requests from a UI click handler.

The state model records scheduled items by clip ID, platform, scheduled time, and status (`pending`, `published`, `failed`). Optimistic UI should show pending state before the final platform confirmation.

## 3.8 Content library / recent history

The app state holds a history list with:

- ID.
- Title.
- Date.
- Recent action, examples “Edit Short” or “Search for Shorts”.
- Icon type: `youtube`, `clip`, or `project`.

The Google Drive proposal organises files under a `CLIPIN_Content` root, separated by platform and publication status. The exact folder structure is reproduced in the integration section below.

---

# 4. YouTube-specific functionality

## 4.1 YouTube URL input

The UI explicitly instructs users to paste a YouTube URL (and, depending on the screen, TikTok, Instagram or Google Drive URL). The title-generator screen specifically says: **“Start by pasting your YouTube or Google Drive link below.”**

Its context fields include:

- Inspiration YouTube channel handle.
- Trending country.
- Optional additional context.
- Generate Title CTA.

Results are AI-generated title variants shown as selectable cards.

## 4.2 YouTube Shorts as a target format

YouTube Shorts appears in:

- Platform-aware clip extraction.
- Vertical 9:16 output formatting.
- Hook generation (`shorts` is one of the platform values in a later prompt/API contract).
- Title, description, chapters, tags and subtitle cleanup utilities.
- Content scheduling and publishing architecture.
- Google Drive storage hierarchy (`YouTube/Shorts/ReadyToPost`).

The source does not document a dedicated video downloader implementation or a complete media-transcoding pipeline. That remains an implementation gap between the YouTube URL field and a ready-to-export clip.

## 4.3 YouTube Data API v3 upload proposal

File: `lib/youtube-api.ts`.

A proposed function `uploadYouTubeShort` takes:

```ts
{
  accessToken: string;
  videoPath: Buffer | ReadableStream;
  title: string;
  description: string;
  tags: string[];
  scheduledFor?: Date;
}
```

The prior example describes using YouTube's resumable upload protocol at:

`https://www.googleapis.com/upload/youtube/v3/videos?uploadType=resumable&part=snippet,status`

Metadata in the example:

- `snippet.title`
- `snippet.description`
- `snippet.tags`
- `snippet.categoryId: '22'` (comment says People & Blogs)
- `status.privacyStatus`: `private` when scheduled, otherwise `public`
- `status.publishAt`: ISO string for a scheduled post
- `selfDeclaredMadeForKids: false`

The proposed steps are to initiate a resumable upload, receive an upload URI, upload the binary in chunks, and return a video ID.

Recorded OAuth scope:

`https://www.googleapis.com/auth/youtube.upload`

The same historical document includes claims about daily quota, upload units, verified-channel limits and cost. These are historical source claims and need current official documentation checks before being used for budgeting or production design.

## 4.4 Other YouTube content tools

### Titles
- Request can include video URL, topic, transcript, inspiration channel, trending country, additional context, platform and count.
- Default count: five.
- Produces accurate, intriguing, platform-aware title options, using curiosity gaps, pattern interrupts and social-proof signals as prompting concepts.
- AI-layer task uses `video_title`; output objects contain title, character count, SEO-strength label (high/medium/low), and reasoning.

### Descriptions
- Description generation is a named API/task.
- Intended to create engaging, search-optimised copy with timestamps and calls to action where appropriate.
- One description API map returns a string; later AI prompt registry models it as structured content. The canonical contract needs to be standardised.

### Chapters
- Generates timestamped sections.
- AI service inputs: title, transcript and total duration in seconds.
- Use case: YouTube chapters.
- The output should contain MM:SS timestamps with section titles, according to the architecture guide.

### Tags and keywords
- Generates relevant hashtags/keywords; the source says 10–15.
- Inputs include title, topic, platform and niche.
- YouTube/TikTok optimisation is named as an intended use.

### Script writing / outline / rewrite
- Script writing accepts topic, duration, audience, tone, optional source URL and context.
- Supported formats in the API spec: short-form, long-form, listicle and story.
- Supported tones in one contract: educational, entertaining, inspirational, conversational.
- Script includes hook, introduction/body sections, timing cues and CTA.
- Outline produces hook, timed sections, conclusion and CTA.
- Rewrite preserves core subject matter while improving clarity, pacing and engagement for a target platform and audience.
- A rewrite-from-video task is included in the tool hub.

### Hooks
- Generates 5–10 hooks designed to capture attention in the first three seconds.
- Later schema hook types: question, statement, curiosity gap, pattern interrupt, emotional.
- Earlier platform examples: shock question, roast setup, relatable, drama tease, community call.
- Example phrases recorded in source include Nigerian Pidgin/localised forms such as “ICPC recover wetin?!”, “Na who go survive this wahala?”, and “Who dey claim this?”. These are examples of tone/patterns, not mandatory copy.

### Subtitles
- Input is SRT-formatted subtitle text.
- Output is grammar-corrected, readable subtitles.
- The prompt/task is named `subtitle_cleanup`.
- The architecture should distinguish improving readability from changing the original meaning or timing; the legacy spec does not fully spell out that preservation policy.

---

# 5. Entire AI feature inventory recovered

The prompt registry defines 12 task IDs:

1. `clip_candidates`
2. `video_ideas`
3. `hooks`
4. `script_write`
5. `script_outline`
6. `script_rewrite`
7. `video_title`
8. `video_description`
9. `video_chapters`
10. `video_tags`
11. `subtitle_cleanup`
12. `clip_quality_review`

The service layer also exposes topic research/crawling and a batch content operation.

## 5.1 Video ideas

- Input: topic, platform, audience, optional niche and context.
- Produces five unique actionable concepts.
- Each idea can contain title, concept, opening hook, suggested format (short/medium/long), estimated duration, platform and trend alignment.
- Prompt temperature in the recorded registry: 0.8; max token budget 1,500.

## 5.2 Hooks

- Input: topic, platform, audience, format, context.
- Produces 5–10 hooks, each typed and accompanied by advice on usage.
- Registry temperature: 0.85; token budget: 1,200.

## 5.3 Script writer

- Input: topic, duration in seconds, audience, tone, optional source URL and context.
- When a source URL is supplied, the service attempts to crawl it and formats the retrieved material as LLM context. Crawl errors are logged and the script-writing task can continue with the remaining context.
- Structured output: title, hook, introduction, numbered sections with headings/content/timing, CTA, estimated duration.
- Token budget in registry: 2,000.

## 5.4 Script outline

- Input: topic, duration, audience and context.
- Output: hook, numbered sections, titles, key points, timing, conclusion and CTA.
- Token budget in registry: 1,500.

## 5.5 Script rewrite

- Input: original script/transcript, target platform, audience and tone.
- Output: rewritten script, key changes, and improved aspects with explanation.
- Goal: improve clarity, pacing and engagement while preserving core subject matter.
- Token budget: 2,000.

## 5.6 Video title

- Input in the registry: topic, platform, audience and context.
- Output: five title variants, character counts, SEO strength and reasoning.
- Separate API contract also supports video URL/transcript, inspiration channel, country and result count.
- Token budget: 800.

## 5.7 Video description

- Intended to produce engaging, search-aware descriptions with timestamps and CTAs where appropriate.
- API response type is inconsistent across the two source documents (string versus structured output); consolidate before production.

## 5.8 Video chapters

- Input: title, transcript, total duration.
- Output: timestamped sections; intended for YouTube chapters.

## 5.9 Video tags

- Input: title, topic, platform and niche.
- Output: 10–15 relevant keywords/hashtags in the implementation guide.

## 5.10 Subtitle cleanup

- Input: SRT string.
- Output: corrected, readable subtitle text.

## 5.11 Clip quality review

- Input: duration, platform, hook and transcript.
- Intended output: quality/virality scores and feedback.
- A reviewed clip can be scored before export, allowing a user to compare candidates.

## 5.12 Topic research / crawling

- Input: source URL, topic and optional crawl config.
- Crawls allowed pages, reports pages succeeded/failed, and formats research content for an AI task.
- Includes URL validation, domain allowlist, private IP blocking, HTTP/HTTPS-only policy, rate limiting, robots.txt/x-robots-tag handling, content extraction, chunking and deduplication.

## 5.13 Batch content generation

A batch operation concurrently generates titles, tags and video ideas using `Promise.all`, based on topic, platform and audience. The design intends to reduce user friction when a creator needs a package of promotional assets rather than a single output.

---

# 6. Design architecture and design tokens

## 6.1 Two deliberately separate visual modes

The original design specification declares two visual modes that should not be mixed on the same screen:

### Immersive Dark — onboarding only
- Derived from blue-toned onboarding reference screenshots, labelled Images 7–9.
- Used for first-run onboarding, splash screens and feature introductions.
- Full-bleed background photo or gradient.
- Dark teal overlay `rgba(0, 50, 70, 0.72)`.
- White centered line icon, large display title, short subtitle, ghost-outline CTA and slide-pagination dots.
- No light-mode surface tokens on onboarding screens.

### Clean Light — functional tool experience
- Derived from 2short.ai references labelled Images 1–6.
- Used for the hub and functional tools.
- White backgrounds and cards, pale-grey inputs, blue actions, subtle borders/shadows, rounded forms and a restrained information hierarchy.
- The dark onboarding → light tool transition signals that onboarding has ended and work has begun.

The design specification says these modes should not be mixed within the same screen.

## 6.2 Fonts

- Display: **Newsreader**, serif; headers and onboarding hero titles.
- Body/UI: **Inter**, sans-serif.
- Mono: **DM Mono**, monospace; code, timestamps and tags.

## 6.3 Global light-mode tokens

```css
--bg: #FFFFFF;
--bg-surface: #F8F8F5;
--bg-input: #F3F4F6;
--bg-card: #FFFFFF;
--border: #E5E7EB;
--border-subtle: #F3F4F6;
--text-primary: #111827;
--text-secondary: #6B7280;
--text-muted: #9CA3AF;
--text-accent: #3B82F6;
--accent: #3B82F6;
--accent-hover: #2563EB;
--success: #10B981;
--warning: #F59E0B;
--danger: #EF4444;
--pad-screen: 20px;
--pad-card: 16px;
--gap-section: 28px;
--gap-item: 12px;
--r-input: 50px;
--r-card: 16px;
--r-tile: 20px;
--r-sheet: 28px;
--r-btn: 50px;
--r-tag: 50px;
--r-dot: 50px;
--shadow-card: 0 1px 3px rgba(0,0,0,0.07), 0 1px 2px rgba(0,0,0,0.04);
--shadow-sheet: 0 -4px 24px rgba(0,0,0,0.12);
--shadow-tile: 0 4px 14px rgba(0,0,0,0.10);
```

Dark onboarding tokens:

```css
--dark-overlay: rgba(0, 50, 70, 0.72);
--dark-text: #FFFFFF;
--dark-subtext: rgba(255, 255, 255, 0.75);
--dark-border: rgba(255, 255, 255, 0.35);
--dark-dot: rgba(255, 255, 255, 0.45);
--dark-dot-active: #FFFFFF;
```

## 6.4 Tool family gradients

The design spec calls these gradients immutable because they identify tool categories:

- Repurpose — warm red/orange: `linear-gradient(135deg, #FF6B35 0%, #C0392B 100%)`.
- Ideate — amber/brown: `linear-gradient(135deg, #F59E0B 0%, #78350F 100%)`.
- Scripting — teal/dark green: `linear-gradient(135deg, #6EE7B7 0%, #064E3B 100%)`.
- Optimise — indigo/purple: `linear-gradient(135deg, #818CF8 0%, #4338CA 100%)`.
- Monetise — violet/dark: `linear-gradient(135deg, #C084FC 0%, #1E1B4B 100%)`.
- Schedule — ocean blue: `linear-gradient(135deg, #38BDF8 0%, #0C4A6E 100%)`.
- Analyse — slate/charcoal: `linear-gradient(135deg, #94A3B8 0%, #1E293B 100%)`.

## 6.5 Typography scale

- Onboarding display: 32px, bold, Newsreader, line-height 1.15.
- Tool hero: 28px, bold, Inter, line-height 1.2; selected words can use accent blue.
- Section labels: 13px Inter, muted; section icon 16px with reduced opacity.
- Clip-card label: 11px, semibold, uppercase, letter-spacing 0.08em, single-line ellipsis.
- Clip quote: 18px, bold, line-height 1.35, maximum three lines.
- Clip duration metadata: 14px muted (another rule uses 13px in the ClipCard implementation; standardise this inconsistency).
- Input: 15px.
- Button: 15px bold, letter-spacing 0.04em.

---

# 7. Component-by-component UI extraction

## 7.1 OnboardingSlide

- Route: `/onboarding`.
- Three slides, swipe/tap or timed advance.
- Full-bleed image with `background-size: cover` and centered crop; if no photo, a teal/green/indigo gradient is proposed: `linear-gradient(135deg, #0C4A6E 0%, #065F46 50%, #1E1B4B 100%)`.
- Overlay via absolutely positioned `::before` pseudo-element.
- Centered 48px white icon, stroke width 1.5.
- Title: 32px white bold; subtitle 14px white at 0.75 opacity, max width 280px, line-height 1.6.
- Last-slide CTA: transparent, white border, pill radius, 14px 40px padding.
- Dots bottom-centered; inactive dots 8px circles, active dot 28×8px pill.
- Three titles: “One Video. Infinite Clips.”, “Every Platform, Every Day.”, “Flexible to Your Style.”
- “Get Started” navigates to Auth.

## 7.2 PillInput

- Main video URL input.
- Pale-grey background `#F3F4F6`, 50px radius, 14px × 16px padding, link/search icon, flexible input field and optional outlined AUTO tag.
- Prefix icon 18px, muted grey.
- AUTO label 12px bold, 1.5px border, pill shape.
- Typed props: placeholder, prefix icon, suffix tag, suffix callback, value, onChange, onSubmit.

## 7.3 ToolTile

- Square tile: `aspect-ratio: 1/1`, 20px radius, 16px padding, gradient fill, bottom-left aligned white label (17px bold), subtle noise overlay.
- Two-column grid with 12px gap; featured `lg` tile spans full width.
- Hover elevation: translateY(-2px), larger shadow, 0.2s transition.
- Keyboard-focusable and activatable by Enter/Space.

## 7.4 ClipCard

- White card, light border, 16px radius, 16px padding, 10px bottom margin.
- Selected state uses blue border and `#EFF6FF` background.
- Uppercase small label, max one line with ellipsis.
- Transcript quote preview is bold, 18px, max three lines.
- Footer has duration with clock icon and a circular blue arrow CTA.
- Props: index, clip title, quote preview, duration seconds, open callback, selected flag.

## 7.5 BottomSheet

- Used for manual cuts and configuration.
- Fixed overlay, black at 40% opacity; sheet fixed at bottom; white background, 28px rounded top corners, 20px horizontal padding; drag handle, close button and primary CTA.
- Radio options expand content when selected.
- Start/end time fields side-by-side in pale-grey inset box.
- Upgrade link is accent blue.
- Accessibility: focus trap while open, close on Escape, proper focus handling.

## 7.6 FloatingActionBar

- Fixed bottom, centered, dark translucent pill with backdrop blur.
- Icon actions with labels/callbacks: sort, trim/edit and share/download depending on context.
- White icons, 36px hit boxes, 28px gap, opacity increase on hover.

## 7.7 RecentHistoryItem

- Horizontal row, 14px gap, 12px vertical padding, subtle divider.
- 40×40px pale-grey icon tile.
- Truncated title, date/action metadata, circular blue arrow.
- `iconType`: `youtube`, `clip`, `project`.

## 7.8 ContextField

- For inspiration channel/creator, country dropdown and optional context.
- Grey background, 14px radius, 14px × 16px padding, 10px bottom gap.
- Input text 15px, dropdown with right-aligned chevron icon.

## 7.9 SectionHeader

- Category icon and label row.
- 16px icon, grey, stroke width 1.5; label 14px medium, grey.
- Margin 20px vertical top and 12px bottom.

## 7.10 EarningsCalculator

- A dark card inside the light-mode application.
- Platform tabs: TikTok, YouTube Shorts, Instagram, YouTube long-form.
- Inputs: expected monthly views slider, clips per month, follower count, niche, brand-deal inclusion.
- Output ranges for platform revenue, brand deals, CLIPIN performance deal and total monthly estimate, plus EMV-equivalent metric.
- Every output must be a range rather than an over-precise single estimate, according to the prior spec.
- The specified disclaimer must appear on every render.

---

# 8. Detailed screen specifications

## 8.1 Tool Hub

- Routes: `/` or `/app/hub`.
- Clean light visual mode.
- Greeting: “Hey [Name], what will you create today?”
- Subtitle: “Explore our tools and start creating”.
- Category groups: Repurpose, Ideate, Scripting, Upload & Optimise, Monetise, Schedule.
- Recent history sits below the greeting and above tool categories; maximum three items visible; “View all” links to `/app/history`.

## 8.2 Short Clip Maker input

- Route: `/app/clipmaker`.
- Hero: “Ready to create Shorts in seconds?”
- Link source line says YouTube, TikTok, Instagram or Google Drive.
- Context: inspiration channel/creator, trend country and optional additional notes.
- Sticky Generate Clips CTA.
- States: empty, active after URL input, loading/analysing, and validation/error.

## 8.3 Clip Results

- Route `/app/clipmaker/results`.
- Summary of number of found moments.
- Numbered ClipCards.
- Floating action bar includes sort, trim, share all.
- Card selection opens detail sheet.

## 8.4 Clip Detail

- BottomSheet over results page.
- Choose whole source video or manually define start/end.
- Time values shown as HH:MM:SS.
- The source copy uses 10–60 seconds in this screen, which conflicts with other prompt contracts.

## 8.5 Title Generator

- Route `/app/optimise/title`.
- Title with one highlighted blue term.
- Input accepts YouTube or Google Drive link.
- Context fields for inspiration YouTube channel, country and optional details.
- Results in selectable title cards.

## 8.6 Scripting Tools

- Route `/app/script/[mode]` with write, outline and rewrite variants.
- Common shell: URL or topic input, formatted AI output, copy/export controls.

## 8.7 Earnings Calculator

- Route `/app/monetise`.
- Uses a dark calculator widget within the otherwise light platform.
- See section 11 for the historical rate table and explicit disclaimer.

---

# 9. Frontend route and file architecture recorded in source

The proposed Next.js structure is:

```text
src/
├── app/
│   ├── (onboarding)/
│   │   ├── page.tsx
│   │   └── layout.tsx
│   ├── (auth)/
│   │   ├── login/page.tsx
│   │   └── signup/page.tsx
│   ├── (platform)/
│   │   ├── layout.tsx
│   │   ├── page.tsx
│   │   ├── clipmaker/page.tsx
│   │   ├── clipmaker/results/page.tsx
│   │   ├── ideate/page.tsx
│   │   ├── hooks/page.tsx
│   │   ├── script/write/page.tsx
│   │   ├── script/outline/page.tsx
│   │   ├── script/rewrite/page.tsx
│   │   ├── optimise/title/page.tsx
│   │   ├── optimise/description/page.tsx
│   │   ├── optimise/chapters/page.tsx
│   │   ├── optimise/tags/page.tsx
│   │   ├── monetise/page.tsx
│   │   ├── schedule/page.tsx
│   │   └── history/page.tsx
├── components/
│   ├── onboarding/OnboardingSlide.tsx
│   ├── onboarding/OnboardingDots.tsx
│   ├── ui/PillInput.tsx
│   ├── ui/ToolTile.tsx
│   ├── ui/ClipCard.tsx
│   ├── ui/BottomSheet.tsx
│   ├── ui/FloatingActionBar.tsx
│   ├── ui/RecentHistoryItem.tsx
│   ├── ui/ContextField.tsx
│   ├── ui/SectionHeader.tsx
│   ├── layout/BottomNav.tsx
│   ├── layout/TopBar.tsx
│   └── tools/
│       ├── ClipResultsList.tsx
│       ├── ScriptOutput.tsx
│       └── EarningsCalculator.tsx
├── hooks/
│   ├── useOpenRouter.ts
│   ├── useVideoAnalysis.ts
│   └── useScheduler.ts
├── lib/
│   ├── openrouter.ts
│   ├── tiktok-api.ts
│   ├── instagram-api.ts
│   ├── youtube-api.ts
│   └── drive-api.ts
└── types/
    ├── clip.ts
    ├── tool.ts
    └── api.ts
```

The subsequent AI-layer transcript proposes additional modules under `src/lib/ai/`, listed below. The front-end screen map and AI-layer structure need to be reconciled against the live repository before implementation.

---

# 10. AI / OpenRouter architecture

## 10.1 Proposed processing chain

```text
React Component
  → Next.js Server Action / API route
  → AI Service Facade
  → Task Executor
      → Prompt Registry lookup
      → Input validation
      → Prompt construction
      → Structured output parsing/validation (Zod)
      → Retry and fallback handling
      → Usage/token tracking
  → OpenRouter provider
  → Structured result back to UI
```

The design deliberately separates each task's prompt from execution logic. Each task has an ID, version, system instructions, user prompt template, optional context instructions, injection defense, output schema, model/token configuration, and optional fallback.

## 10.2 OpenRouter gateway

The source defines a server-only provider using `@ai-sdk/openai-compatible`, with base URL `https://openrouter.ai/api/v1`, Bearer API key, optional site URL/name headers, and configurable model name in `provider/model-name` format. It specifies:

- Lazy provider initialization.
- Default model in the historical example: `openai/gpt-4-turbo`.
- Default request timeout: 60 seconds.
- Default maximum tokens: 2,048.
- Temperature: 0.7; topP 1; frequency/presence penalty 0.
- Retry count 2, delay 1,000ms in base config.
- Optional Zod schema on requests.
- Response usage fields for input, output, total tokens, and optional cost.
- Structured response metadata: data, usage, model, provider, timestamp and token counts.
- Streaming and tool-call support mentioned in provider comments.

The other design spec contains a more direct `fetch` implementation against `/chat/completions` with a streaming variant. These implementations are alternatives from separate artifacts; they should be unified, not duplicated blindly.

## 10.3 Prompt registry task IDs

```ts
type AITaskId =
  | 'clip_candidates'
  | 'video_ideas'
  | 'hooks'
  | 'script_write'
  | 'script_outline'
  | 'script_rewrite'
  | 'video_title'
  | 'video_description'
  | 'video_chapters'
  | 'video_tags'
  | 'subtitle_cleanup'
  | 'clip_quality_review';
```

Prompt configs are described as task-scoped, versioned, provider-agnostic, schema-validated, configurable for token budgets/model choices, and injection-resistant. The prior instructions say old prompt versions should be retained; new versions should be added as separate files and registry entries rather than silently replacing historical ones.

## 10.4 Injection defence recorded in the prompt registry

The prior prompt template tells the AI layer not to execute code or system commands, access external systems, change its instructions, follow hidden instructions in user input, or exceed its task scope. It requires structured output matching the task schema.

This is a useful prompt-level boundary, but it is not a complete security control. External URLs, credentials, publishing privileges, filesystem operations, and all consequential actions still require deterministic server-side controls and allowlisted tool contracts.

## 10.5 Task executor behavior

The proposed `executeAITask` pipeline:

1. Checks the task ID and obtains its config.
2. Builds the user prompt by replacing template variables.
3. Merges default request configuration with overrides.
4. Obtains the configured OpenRouter provider/model.
5. Calls the model with a structured schema when configured.
6. Validates/parses structured output.
7. Returns success/data or a structured error, model name, timestamp and usage.

A retry wrapper retries with exponential backoff. Other named helpers include batch execution, streaming, and input validation. The transcript says parse errors are handled/fallbacks are supported; exact limits and semantics should be confirmed in the live code.

## 10.6 AI service facade functions

Functions named in the recovered AI service layer:

- `generateClipCandidates`
- `generateVideoIdeas`
- `generateHooks`
- `writeScript`
- `outlineScript`
- `rewriteScript`
- `generateVideoTitles`
- `generateVideoDescription`
- `generateVideoChapters`
- `generateVideoTags`
- `cleanupSubtitles`
- `reviewClipQuality`
- `researchTopic`
- `batchGenerateContent`

The facade maps domain inputs into prompt registry variables and calls task execution/retry helpers. `writeScript` optionally crawls a source URL to enrich its context; if crawling fails, it logs a warning and proceeds with available context.

## 10.7 Model routing historical proposal

One version of the design specifies:

- Fast: `openai/gpt-4o-mini` for titles, tags, short descriptions.
- Standard: `anthropic/claude-3-5-haiku` for scripting, descriptions and hooks.
- Premium: `anthropic/claude-3-5-sonnet` for full rewrites, chapters and long-form analysis.
- Structured JSON: `openai/gpt-4o-mini`.
- Vision: `openai/gpt-4o` for uploaded thumbnails/screenshots.

A later/other environment setup defaults to `openai/gpt-4-turbo` and lists older examples such as GPT-4, Claude 3 Opus/Sonnet, Gemini Pro and Llama 2 70B. These are historical configuration examples, not a current recommendation. The final implementation should use currently supported model IDs, capability checks and a task-specific cost/quality routing policy.

## 10.8 Token budgets recorded per prompt

- Video ideas: 1,500 tokens, temperature 0.8.
- Hooks: 1,200 tokens, temperature 0.85.
- Script writing: 2,000 tokens, temperature 0.7.
- Script outline: 1,500 tokens, temperature 0.7.
- Script rewrite: 2,000 tokens, temperature 0.7.
- Titles: 800 tokens, temperature 0.8.
- Clip candidates: 2,048 tokens, temperature 0.7.

Other tasks have configs in the source, but these are the explicit values recovered directly from the visible excerpts.

---

# 11. API / integration inventory

## 11.1 OpenRouter

Purpose: AI clip extraction, ideation, hooks, scripts, title generation, descriptions, chapters, tags, subtitles, quality review and research-related generation. Auth: server-side Bearer token. All requests should pass through a server route/action; no API key in browser code.

## 11.2 TikTok

Historical proposal base: `https://open.tiktokapis.com/v2`.

Function: `postToTikTok` with access token, video path, caption, hashtag names, optional scheduled time and privacy level. The example starts a video publish upload using `/post/publish/video/init/`, then uploads the binary and polls publish status. It includes a 150-character title/caption substring, privacy choice, comment/duet/stitch flags, cover timestamp and chunked upload metadata.

Recorded OAuth scopes: `video.publish`, `video.upload`.

The document includes daily limits, request rates, cost, and scheduling-window figures labelled “verified 2026”. Those are unverified historical assertions here and must be checked against current official documentation and the app's approved API access before implementation.

## 11.3 Instagram Graph API

Historical proposal base: `https://graph.facebook.com/v20.0`.

Function: `postInstagramReel` with long-lived access token, IG user ID, publicly accessible video URL, caption, `shareToFeed` and optional scheduled publish time. Flow: create a media container with `media_type: 'REELS'`, poll status until `FINISHED`, then call `media_publish` with the container ID.

Recorded permissions: `instagram_basic`, `instagram_content_publish`.

The source also includes API quota/cost/scheduling assertions that must be verified with current Meta documentation and account eligibility.

## 11.4 YouTube Data API v3

Upload via resumable upload; metadata includes title, description, tags, category, privacy state, scheduled publish time and made-for-kids declaration. OAuth uses `youtube.upload`. Video file binary is uploaded in chunks after creation of the resumable upload URI. Returns video ID.

Current support for publishing/scheduling, quota cost, project verification, and allowed upload behavior should be verified against official API documentation; the prior document's numeric limit claims should not be treated as current without research.

## 11.5 Google Drive

Purpose: content storage and retrieval, plus staged files for platform upload. Proposed structure:

```text
CLIPIN_Content/
├── TikTok/
│   ├── ReadyToPost/
│   ├── PendingApproval/
│   └── Archive/
├── Instagram/
│   ├── Reels/ReadyToPost/
│   ├── Stories/ReadyToPost/
│   └── Feed/ReadyToPost/
└── YouTube/
    ├── Shorts/ReadyToPost/
    └── Community/ReadyToPost/
```

The `listReadyFiles` proposal chooses a folder by platform/content type, filters MIME types to video, and sorts by creation time descending.

## 11.6 Whisper / transcript generation, FFmpeg and Remotion

The environment template mentions as future configuration options:

- `WHISPER_API_KEY` — for transcription.
- `FFMPEG_PATH` — for media processing.
- `REMOTION_API_KEY` — for render/video generation.

This suggests an intended future pipeline for obtaining transcripts and generating or transforming video, but the original specification does not show a complete implemented transcription, download, video-processing or rendering pipeline. Treat it as a required architecture area, not a verified existing feature.

## 11.7 Database, queue, storage

Future environment examples:

- PostgreSQL `DATABASE_URL`.
- Redis `REDIS_URL`.
- AWS S3 bucket and access credentials.

The AI implementation roadmap also lists Redis caching, Bull/BullMQ worker queue, rate limiting per user/workspace, webhooks for audit trails, multi-provider fallback and cost tracking as future extensions. Publishing jobs are already specified conceptually as queue-backed with retry logic; the concrete persistent queue implementation remains to be verified.

---

# 12. Environment configuration collected from source

The recovered source lists these variables as examples:

```bash
# OpenRouter — server only
OPENROUTER_API_KEY=...
OPENROUTER_MODEL=...
OPENROUTER_SITE_URL=http://localhost:3000
OPENROUTER_SITE_NAME=CLIPIN

# TikTok
TIKTOK_CLIENT_KEY=...
TIKTOK_CLIENT_SECRET=...

# Meta / Instagram
META_APP_ID=...
META_APP_SECRET=...

# Google / YouTube / Drive
GOOGLE_CLIENT_ID=...
GOOGLE_CLIENT_SECRET=...
# App
NEXT_PUBLIC_APP_URL=https://clipin.app
NEXT_PUBLIC_APP_NAME=CLIPIN

# Feature flags
NEXT_PUBLIC_ENABLE_SCHEDULING=true
NEXT_PUBLIC_ENABLE_DRIVE_SYNC=true

# Proposed future video-processing and storage values
WHISPER_API_KEY=...
FFMPEG_PATH=/usr/bin/ffmpeg
REMOTION_API_KEY=...
DATABASE_URL=postgresql://user:password@localhost:5432/clipin
REDIS_URL=redis://localhost:6379
AWS_S3_BUCKET=...
AWS_ACCESS_KEY_ID=...
AWS_SECRET_ACCESS_KEY=...
```

Secrets must be stored server-side and out of version control. The `NEXT_PUBLIC_` prefix is appropriate only for non-secret browser-visible values such as public app URL/name and feature flags—not credentials. The original source explicitly forbids exposing OpenRouter, TikTok, Meta or Google secrets to the client.

---

# 13. State management and data model

The source defines this broad client/app state shape:

```ts
interface AppState {
  user: {
    id: string;
    name: string;
    email: string;
    plan: 'free' | 'creator' | 'growth' | 'agency';
    credits: number;
    creditsTotal: number;
  };
  currentSession: {
    videoUrl: string | null;
    transcript: string | null;
    clips: ClipMoment[];
    selectedClipIndex: number | null;
    contextHints: {
      inspirationChannel: string;
      trendingCountry: string;
      additionalContext: string;
    };
  };
  history: Array<{
    id: string;
    title: string;
    date: string;
    action: string;
    iconType: 'youtube' | 'clip' | 'project';
  }>;
  schedule: Array<{
    clipId: string;
    platform: string;
    scheduledFor: Date;
    status: 'pending' | 'published' | 'failed';
  }>;
}
```

This is a UI/global state proposal, not a complete normalized database schema. Production work still needs persisted entities and ownership rules for users, videos, transcripts, candidate clips, generated assets, exports, scheduled posts, provider accounts, job state, AI usage, prompt versions and audit logs.

---

# 14. Navigation

## Bottom navigation

Five tabs on light-mode app screens:

| Tab | Icon | Route |
|---|---|---|
| Hub | Home | `/` |
| Clips | Scissors | `/app/clipmaker` |
| Schedule | Calendar | `/app/schedule` |
| Stats | Bar chart | `/app/analytics` |
| More | Grid | `/app/more` |

Active tab: blue icon and label. Inactive: grey icon, no label.

## Top bar

- CLIPIN logo, bold 18px Inter, dark text.
- Notification bell with red dot for unread notifications.
- User avatar, initial in dark-green circle (reference noted as coming from the WeClip OS design).

---

# 15. Monetisation and earnings calculator

## 15.1 Proposed inputs

- Platform: TikTok, YouTube Shorts, YouTube long-form, Instagram.
- Views per month.
- Clips per month.
- Include brand deals toggle.
- Follower count.
- Niche.

## 15.2 Output structure

- Platform revenue low/high.
- Brand-deal revenue low/high.
- CLIPIN performance-deal revenue low/high.
- Total monthly earnings low/high.
- EMV-equivalent metric, described in the source using a $5 CPM assumption.
- Save Estimate action.

## 15.3 Historical rate table included in the source

The architecture document labels these as “Verified Rate Table (2026 Research)”:

| Platform/category | Metric | Low | High | Note recorded in source |
|---|---|---:|---:|---|
| TikTok Creator Rewards | RPM per 1K views | $0.40 | $1.00 | “Top creators: up to $2.00” |
| TikTok Creator Rewards | Per 1M views | $400 | $1,000 | Requires Creator Rewards Program |
| YouTube Shorts | RPM per 1K views | $0.03 | $0.07 | Revenue share since Feb 2023 |
| YouTube Shorts | Per 1M views | $30 | $70 | — |
| YouTube long-form | RPM per 1K views | $1.00 | $10.00 | Varies heavily by niche |
| Instagram Reels direct monetisation | — | ~$0 | ~$0 | Source says bonus program discontinued Mar 2025 |
| Instagram Reels brand deals | Per 1K | $5 | $12 | Primary income path in source |
| Sponsored clip (micro) | Per post under 50K | $100 | $500 | Brand deal |
| Sponsored clip (macro) | Per post 1M+ | $5,000 | $10,000 | Brand deal |
| CLIPIN performance deal | Per 1M views | $300 | $1,500 | Platform-specific deal |

**Evidence caution:** These numbers are copied from a past project artifact and have not been verified in this extraction. Do not present them as reliable current rates or base financial decisions on them until each rate, date, eligibility condition and geography has been re-researched from trustworthy current sources.

## 15.4 Required disclaimer in original spec

> These are estimated projections based on 2026 average platform rates. Actual earnings depend on niche, audience quality, engagement rate, geographic reach, and brand deal availability. EMV calculated at industry-standard $5 CPM.

The disclaimer was mandated on every render. As the underlying figures may be outdated or not applicable to every creator, the product should dynamically label assumptions, dates and eligibility rather than repeat a static claim of verification.

---

# 16. Accessibility and performance requirements

## 16.1 Accessibility

The CLIPIN spec lists:

- Every interactive control must have an `aria-label` or visible label.
- Text contrast against backgrounds must meet WCAG AA; the document specifies at least 4.5:1.
- PillInput supports Enter-key submission.
- BottomSheet closes on Escape and traps focus when open.
- ToolTile is keyboard-focusable and responds to Enter/Space.
- Pagination dots announce “Slide X of Y”; active dot has `aria-current="true"`.
- Loading containers use `aria-busy="true"`.
- Platform icons have descriptive alt text.
- Correct focus management is required for modal/sheet transitions.

## 16.2 Performance

Recorded targets and rules:

- First Contentful Paint under 1.5 seconds on 4G (target in the historical spec; needs measured testing).
- Clip results lists over 20 items should be virtualised, using `react-virtual` in the source.
- OpenRouter response streams should render progressively rather than wait for completion.
- Google Drive files should be paginated at 20 per request.
- Platform API calls should show optimistic pending states.
- Tool-tile hover should use `will-change: transform` only for hover/animation as suggested.

---

# 17. Security and reliability principles

These controls are explicit in the previous AI guide or product spec:

1. Never expose API keys in the client bundle.
2. Route AI and publishing API calls through the server.
3. Validate structured AI output with Zod before using it in components or subsequent operations.
4. Wrap JSON parsing in error handling where required.
5. Use retry logic with exponential backoff for appropriate transient failures.
6. Support fallback output where configured.
7. Validate URLs before crawling; allow HTTP/HTTPS only.
8. Use a domain allowlist for content research, block private IP ranges, rate-limit crawling, and respect robots.txt/x-robots-tag.
9. Keep each AI task scoped to a versioned prompt and declared output schema.
10. Do not let text from external content override system instructions or authorize tools.
11. Schedule publishing through a queue with retry logic rather than direct click-handler calls.
12. Track AI usage, token consumption, model and timestamp.
13. Use safe error handling and never silently equate a malformed AI result with success.
14. Verify authorization scopes, user account connections, content ownership, and publish permissions before posting.

The original source mainly sketches prompt-level injection defence and URL/crawler controls. It does not fully document access-control enforcement, content-rights checks, provider-token lifecycle, tenancy isolation, idempotent publishing, audit schema, deletion/retention, rate limiting across users, or a robust media sandbox. These remain production requirements to design and test.

---

# 18. Implementation history and actual status boundaries

The recovered AI transcript narrates a proposed implementation of:

- `src/lib/ai-gateway.server.ts`
- `src/lib/ai/prompt-registry.ts`
- `src/lib/ai/task-executor.ts`
- Crawl-engine functions including URL validation, content extraction, crawling, chunking, deduplication and formatting.
- `src/lib/ai/ai-service.ts`
- `src/lib/ai/README.md`
- `.env.example`
- `docs/AI-IMPLEMENTATION-GUIDE.md`

The AI guide says the MVP includes OpenRouter, structured output validation, prompt versioning, retries with exponential backoff and safe crawling with SSRF protection. It lists these future items:

- LangChain/LlamaIndex integration.
- Vector embeddings.
- Redis caching.
- Bull/BullMQ worker queue.
- Multi-provider fallback (Anthropic/Google).
- Prompt A/B-testing framework.
- Cost-tracking dashboard.
- Per-user/workspace rate limiting.
- Webhook audit logging.

The transcript includes “accepted the action”/“proceed” messages and code proposals. **No live repository checkout, commit history, deploy log or test report was inspected as part of this extraction.** Therefore the above should be read as documented design/implementation activity, not verified current repository status.

---

# 19. Conflicts, gaps and anti-assumptions to resolve

## 19.1 Clip duration inconsistency

The recovered body contains several targets:

- UI bottom sheet: 10–60 seconds.
- Main extraction endpoint: minimum 15, maximum 60 seconds by default.
- AI prompt registry: 15–90 seconds.
- Earlier high-level platform summary: 15–60 seconds.

**Decision needed:** Define product constraints per platform and mode. For example, distinguish target duration from user-selectable maximum, but do not pick final limits until current product/platform needs are confirmed. Make them configuration-driven rather than scattered constants.

## 19.2 Number of clip candidates

- Endpoint default: up to 10 candidates.
- AI prompt registry: 3–5 candidates.

**Decision needed:** Standardise `candidateCount` and distinguish the default number from maximum allowable output.

## 19.3 Output schemas disagree

The design API spec uses `index`, `clipTitle`, `quotePreview`, `startTimeSeconds`, `endTimeSeconds`, `durationSeconds`, `hookScore`, `hookPattern`, `recommendedPlatforms`, and optional `suggestedCaption`.

The AI registry uses `momentNumber`, string timestamps, duration, hook, exact transcript, virality score, reasoning, suggested platform, and summary.

**Decision needed:** Define one canonical domain schema and adapters from model/provider formats. Keep score naming, timestamps and platform enums consistent.

## 19.4 YouTube link to actual media processing

The UI accepts YouTube links; candidate generation expects a transcript, and upload uses a video buffer/stream. The source doesn't show a complete, verified source-ingestion/transcription/transcoding path.

**Decision needed:** Explicitly choose the lawful and technically supportable ingestion method, supported URL types, transcription provider, job states, media storage and clip-rendering stack. Do not assume a public URL grants permission to download or republish content.

## 19.5 AI score claims

“Virality score”/“hook score” may help triage candidates, but the source supplies no validated benchmark proving that scores predict views or engagement.

**Decision needed:** Treat scores as model estimates until tested against labelled human evaluations and later performance outcomes. Record calibration and limitations.

## 19.6 APIs and quotas

Specific historic quota/cost figures are included for TikTok, Instagram and YouTube. They may be stale or not universally applicable.

**Decision needed:** Check current official API policies, scopes, app review status, product eligibility, region restrictions, quota rules and scheduling support. Store these as versioned integration facts with last-verified time and source.

## 19.7 Monetisation figures

Historical creator-revenue figures are called “verified 2026” in the source but are not supported with references in the recovered section.

**Decision needed:** Do fresh research, record source/date/market/eligibility, and surface ranges with assumptions and disclaimers.

## 19.8 Prompt registry versus provider configs

Two model-routing systems appear, one using named tiers (`fast`, `standard`, `premium`, `json`, `vision`), the other a single default environment model.

**Decision needed:** Reconcile them into one routing layer with configurable task-to-model mappings, capability requirements, fallback rules and cost/latency controls.

## 19.9 Description and chapters schema

The API route map and prompt registry differ in whether some outputs are strings, Markdown or structured objects.

**Decision needed:** Define explicit response schemas for each endpoint and test them end-to-end.

## 19.10 Design mode mixing

The prior design forbids mixing immersive-dark onboarding and clean-light functional screens on one screen, but the earnings calculator is allowed to be a dark card inside light mode.

**Interpretation:** The rule appears to prohibit mixing the *entire onboarding visual mode* into tool screens, not every dark component. Document that distinction as a design token/system rule.

## 19.11 User and content rights

The original specification does not contain a complete rights/permission workflow for source videos, audio, subtitles, or reposting to destination platforms.

**Decision needed:** Add user confirmation of rights/permission, source attribution where appropriate, and safe handling for restricted, private, deleted or non-downloadable videos.

---

# 20. Canonical product architecture suggested by the extracted body

This is a consolidation proposal, not a claim that all components already exist.

```text
CREATOR UI (Next.js)
  ├─ Onboarding & Auth
  ├─ Tool Hub
  ├─ Clip Maker
  ├─ Clip Results / Editor
  ├─ Scripting & Optimisation
  ├─ Monetisation
  ├─ Scheduling / History / Analytics
  └─ Settings / Connected Accounts
        │
        ▼
SERVER API / ACTION LAYER
  ├─ Input validation / auth / tenancy checks
  ├─ Video-source resolver
  ├─ Transcription and media metadata
  ├─ Clip candidate service
  ├─ Prompt registry / task router
  ├─ AI execution / schema validation
  ├─ Render/transcode pipeline
  ├─ Storage and asset management
  ├─ Publishing job orchestration
  └─ Audit, usage, metrics and errors
        │
        ├──────────────► OpenRouter / LLM provider(s)
        ├──────────────► Transcription provider (Whisper proposed)
        ├──────────────► FFmpeg / Remotion (proposed media stage)
        ├──────────────► Google Drive / object storage
        ├──────────────► YouTube Data API
        ├──────────────► Instagram Graph API
        └──────────────► TikTok Content Posting API

DATA / EXECUTION (proposed, exact stack unresolved)
  ├─ Users and connected accounts
  ├─ Source videos and transcript references
  ├─ Clip candidates and editable in/out points
  ├─ Rendered assets / platform variants
  ├─ Schedule and publishing jobs
  ├─ Prompt registry and versions
  ├─ AI usage/cost records
  └─ Audit events / job state / retry history
```

## Core runtime path proposed

`Source URL or uploaded media → validate source and permissions → resolve metadata/media access → transcribe or obtain transcript → generate candidates → validate candidate schema/timestamps → allow human selection/edit → render platform variants → persist asset → prepare title/caption/tags → queue export/publishing → receive platform outcome → update history and analytics`.

This runtime is a recommended reconciliation of the two source artifacts. The full chain was not demonstrated as a tested, working pipeline in the retrieved materials.

---

# 21. Roadmap derived from the recovered material

## P0 — Confirm product baseline
- Inspect repository branch and current implementation.
- Reconcile the canonical `ClipMoment` schema and duration rules.
- Define supported URL/media ingestion paths and rights policy.
- Select output formats, aspect ratios and render requirements.

## P1 — Make AI task contracts deterministic
- Finalise all 12 prompt configurations.
- Validate requests and outputs with Zod at runtime.
- Unify model routing and fallback behavior.
- Add prompt versioning and regression fixtures.

## P2 — Complete source ingestion/transcription
- Validate video URL and platform source.
- Obtain accessible video metadata and transcript.
- Make external media retrieval safe, permitted and observable.
- Add job state, timeouts, cancellation and retry policy.

## P3 — Complete the clip candidate/editing experience
- Generate timestamped candidates.
- Display quotes, titles, durations, scores and rationale.
- Implement the manual-cut bottom sheet.
- Validate in/out boundaries against source duration.
- Let the user accept/edit/reject candidates before rendering.

## P4 — Implement render/export/storage
- Define vertical and any other platform formats.
- Render with selected approved media tooling.
- Persist source references, transcript, candidate metadata and outputs.
- Add download, share, and platform-ready file packages.

## P5 — Connect publishing and scheduling
- Confirm official API access and platform scopes.
- Queue jobs with retry, idempotency and approval behavior.
- Add status polling/webhooks if available.
- Update schedules and history only on observed platform outcomes.

## P6 — Finish creator tools
- Ideas, hooks, scripts, titles, descriptions, chapters, tags and subtitle cleanup.
- Batch content generation.
- Search research/crawl tool.
- Earnings calculator only after current data validation.

## P7 — Production quality
- Accessibility and responsive UI testing.
- Load/performance checks.
- API error/retry/cancellation tests.
- Tenant/auth security and secrets validation.
- Prompt-injection and untrusted transcript/content tests.
- Usage/cost observability.
- End-to-end tests for source → clip → render → export/publish.

---

# 22. Acceptance criteria to turn the historic plans into verified product behavior

## Clipping accuracy
- All clip timestamps parse and fall within the source duration.
- `endTime > startTime` and duration matches `end-start` within an explicit tolerance.
- Candidate transcript excerpt is traceable to the source transcript.
- Candidate output conforms to the canonical schema.
- Unsupported or missing transcripts produce a clear error or an explicit fallback flow.
- The user can inspect and adjust the selected segment before rendering.

## UI and interaction
- URL input, context fields, empty/loading/error/success states work on mobile and desktop.
- Each ClipCard displays title, quote preview and duration correctly.
- Selecting a card reliably opens detail editing for that clip.
- Manual start/end fields are validated and accessible.
- BottomSheet traps focus and closes using Escape; focus returns to invoking control.
- Result lists are virtualised at the agreed threshold.
- Exact required title/description/caption text is not silently rewritten by the UI.

## AI output quality
- Prompts are versioned.
- Inputs and outputs are validated.
- Candidate scores are labelled estimated, not factual outcomes.
- Transcript excerpts do not invent text.
- Retries do not duplicate side effects.
- Malformed output does not show as successful completion.
- Token/model usage is logged without leaking sensitive prompts or credentials.

## Publishing
- A user has connected and authorised the target platform.
- The rendered video meets configured platform format requirements.
- Publishing occurs through an approved queue and supported API route.
- A post is marked published only after affirmative platform evidence.
- Failures remain visible with a recoverable state and non-duplicating retry behavior.

## Data and security
- No provider secret is exposed to browser code.
- URL retrieval blocks prohibited schemes/private-network targets.
- Account/clip ownership is checked server-side.
- User-provided transcripts and scraped pages are treated as untrusted data.
- Source content rights and user authorization requirements are explicit.

---

# 23. Source material and provenance

## Primary recovered artifact A
**Pasted markdown(2).md — “CLIPIN Platform — Design Architecture & API Specification”**. A 57 KB Markdown specification recovered from Library. It holds the CLIPIN overview, visual tokens, component definitions, screen specs, route map, API examples, monetisation widget, state model, accessibility and performance rules.

## Primary recovered artifact B
**Pasted text(20260809-065238).txt**. A 64 KB implementation-oriented conversation artifact. It contains proposed TypeScript modules and examples for OpenRouter gateway, prompt registry, task executor, crawl engine, AI service facade, client/server action, environment variables and implementation guide, plus comments about what is accepted/proposed/next.

## Primary recovered artifact C
**Creative Systems Memory Extraction v1**. Relevant secondary context for how the broader prompt-compiler and state/provenance approach should be kept separate from the CLIPIN feature-specific prompt registry.

## Provenance classifications for this report
- **SOURCE SPECIFICATION:** Content copied or reorganised from the CLIPIN platform architecture artifact.
- **SOURCE IMPLEMENTATION TRANSCRIPT:** Code architecture and task behavior described in the AI implementation transcript.
- **CONSOLIDATION:** Reconciled interpretation linking UI, AI, media ingestion and publishing.
- **OPEN ISSUE:** Contradiction or missing proof that must be resolved.
- **NOT VERIFIED:** Historical numeric, legal, API availability, deployment, repository or runtime claims not independently checked as part of this extraction.

---

# 24. Final state summary

The recovered memory describes a fairly broad creator-workflow product: **CLIPIN is not just a YouTube clipper; it is a proposed long-form-to-short-form repurposing and creator operations platform.** Its central function is identifying timestamped moments from transcripts and turning them into editable clips, with adjacent capabilities for content ideation, production, optimisation, storage, publishing, monetisation and history.

The design direction is explicit: dark immersive onboarding, clean light functional screens, Newsreader/Inter/DM Mono typography, category-specific immutable gradients, reusable ClipCards and BottomSheets, accessible form states, and queue-backed publishing operations.

The AI architecture is also explicitly modular: OpenRouter gateway, versioned per-task prompts, structured Zod schemas, executor/retry/fallback logic, URL-safe crawling, service facade and usage tracking.

The highest-priority engineering gaps are the source-URL-to-transcript/media pipeline, the disagreement between clip duration/count/schema definitions, and the need to re-verify platform API details and historic monetisation figures. A canonical contract and tested end-to-end vertical slice should precede broad feature expansion.