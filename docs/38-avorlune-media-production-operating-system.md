# AVORLUNE Media Production Operating System

**Status:** Proposed operating procedure  
**Last reviewed:** 2026-11-03  
**Production engine:** Genspark Media Studio (initial provider; replaceable)

## 1. Operating principle

Genspark is the generation and creative workspace. AVORLUNE remains the production owner and system of record for the brief, approvals, creative decisions, asset manifest, production state, quality control and delivery record.

Never let a film, campaign or customer project exist only inside one Genspark account or one chat.

## 2. System of record and storage

### GitHub — production documentation
Repository: Sparkmind-obp-off/Admin-overlune

Store:
- Briefs and approved scope.
- Screenplay, episode outlines and scene breakdowns.
- Story Bible text and canon reference index.
- Storyboard descriptions and shot lists.
- Prompts, model/configuration notes and generation log.
- Production state, approvals and change log.
- Asset manifest with file names, checksums when available, dimensions, duration and storage keys.
- QC results and delivery checklist.

Do not store large video masters, private customer uploads, secrets, credentials or personal data in Git.

### Cloudflare R2 — media archive
Use R2 as the preferred long-term object storage after bucket, access policy, lifecycle and backup are configured.

Store:
- Original customer inputs with authorization and retention metadata.
- Approved character/location/product references.
- Storyboard images, keyframes and generated clips.
- Audio, voice-over, music and effects.
- Project exports and final masters.
- Delivery copies and thumbnails.

Use private buckets by default. Share only short-lived or access-controlled links. Do not expose bucket credentials or private object paths in public client code.

### Genspark Media Studio — active production
Use the project board, nodes, connections, Assets, Story Bible, Screenplay, composer and collaboration features while generating and editing. Genspark assets are project-scoped; use Story Bible for reusable cast/world/style references. Download/backup approved media to the AVORLUNE archive at defined milestones.

### Distribution platforms
TikTok, Facebook, Instagram and YouTube are distribution endpoints, not master archives. Upload approved exports; retain original master and editable project separately.

## 3. Standard project structure

Use one project folder per client/project:

PROJECT-ID/
- 00_ADMIN/ — scope, quote reference, approvals, rights and schedule
- 01_BRIEF/ — creative brief and audience
- 02_STORY_BIBLE/ — world, cast, wardrobe, props, voices, camera/edit/sound rules
- 03_SCREENPLAY/ — master script, chapter scripts, dialogue
- 04_STORYBOARD/ — boards, keyframes, shot list
- 05_REFERENCES/ — approved reference images and source notes
- 06_GENERATIONS/ — shot outputs and generation logs
- 07_AUDIO/ — dialogue, VO, music, SFX and licenses
- 08_EDIT/ — timeline notes, captions, motion graphics, project exports
- 09_DELIVERY/ — final master, cutdowns, thumbnails, captions
- 10_ARCHIVE/ — manifest, checksums, retention and handoff notes

## 4. Production phases and approval gates

### Gate 0 — Intake
Capture:
- Customer, objective, audience and platform.
- Deliverable types, quantity, length, aspect ratio, language and deadline.
- Brand/product facts and approved claims.
- Supplied assets and rights/permissions.
- Budget and revision scope.

No generation before the brief and source rights are accepted.

### Gate 1 — Creative development
Produce:
- Creative concept and message.
- Story/advertising structure.
- Reference direction and moodboard.
- Script or screenplay.
- Deliverable matrix.

Obtain approval before creating expensive batches.

### Gate 2 — Story Bible / brand continuity
For recurring characters or worlds, define:
- Character identity and approved face references.
- Wardrobe, hair, makeup and props.
- Locations, time, timeline and relationships.
- Voice identity and language.
- Camera grammar, lighting, color script and editing rhythm.
- Sound, graphics and forbidden deviations.

Mark approved references as canon in Genspark where supported. Attach the Bible to every related project before generating. Connect reference nodes to relevant shot nodes; a Bible alone is not a guarantee if references are not attached or connected.

### Gate 3 — Storyboard and shot plan
- Create 4-grid for simple work or 25-cell for narrative sequences.
- Break the script into scenes and shots.
- Define shot duration, aspect, camera, subject, action, setting, dialogue, audio and transition.
- Approve shot order and keyframes before video generation.

### Gate 4 — Generation
- Start with one low-cost test shot.
- Inspect configuration estimate before every generation batch.
- Use the lowest acceptable model tier for tests; reserve premium models for approved final shots.
- Generate one version first; avoid unnecessary multi-model fan-out.
- Log account/operator, project, date, model, resolution, duration, credit estimate/actual, node reference and output filename.
- Stop and revise inputs when repeated failures or drift occur.

### Gate 5 — Post-production
- Assemble clips in Video composer.
- Use Motion for exact typography, captions, lower thirds, graphics and logo end cards.
- Use Dub/audio lanes for approved dialogue, voice-over, music and effects.
- Verify captions, spelling, timing, audio mix, aspect ratio and export.
- Export Premiere/CapCut project when supported and included.

### Gate 6 — Human QC and customer review
Review:
- Story logic, pacing and continuity.
- Character/product identity.
- Scene-to-scene geography and wardrobe.
- Lip-sync, voice consistency and pronunciation.
- Text, logo, product labels and CTA accuracy.
- Audio clipping, silence, music rights and subtitle sync.
- Frame artifacts, unwanted morphing, flicker and transitions.
- Platform format, safe areas and export integrity.
- Factual claims, disclaimers and legal permissions.

Record defects and decide: accept, manually fix, reshoot or disclose limitation.

### Gate 7 — Delivery and archive
Deliver agreed masters and cutdowns. Save final assets, editable files if included, captions, thumbnails, manifest, approvals and license records. Confirm retention period and deletion policy.

## 5. Continuity and account-credit handoff

### Preferred method: Genspark Productions collaboration
1. Owner creates the Media Studio project.
2. Owner opens Share → Invite collaborators.
3. Invite the authorized collaborator by email.
4. Collaborator accepts and creates their own project on the production.
5. Shared board and live assets remain synchronized; each collaborator has their own conversation and agent.
6. Agent runs are charged to the collaborator's own credits.
7. Allocate chapter/shot tasks explicitly and avoid simultaneous edits to the same shot unless coordinated.

This is the preferred route when the feature is available in the active workspace. Verify access, roles and synchronization before relying on it for a paid deadline.

### Fallback: portable handoff package
If collaboration is unavailable:
1. Export/download approved assets from the source project.
2. Upload media to private R2 archive.
3. Commit documentation and manifest to GitHub.
4. Create a new Media Studio project in the next account.
5. Upload the Story Bible, canon reference images, previous chapter's final frames, screenplay, storyboard and production state.
6. Connect reference nodes to the new shot nodes.
7. Paste the continuation brief.
8. Generate a low-cost continuity test before the full chapter.

A GitHub URL by itself does not automatically import a repository into Media Studio. A TikTok URL is not a substitute for original source footage or continuity references. Upload actual files and relevant text into the new project.

## 6. Standard continuation packet

Every handoff must include:

### PROJECT_STATE.md
- Project ID and title.
- Current phase and approved scope.
- Current chapter/scene/shot.
- Last approved cut and last approved frame.
- Canon references and Story Bible version.
- Outstanding tasks and blockers.
- Approved creative decisions and prohibited changes.
- Next action and acceptance criteria.

### ASSET_MANIFEST.csv or .md
For each file:
- Asset ID.
- File name and storage key.
- Asset type.
- Scene/shot association.
- Version and approval status.
- Dimensions, aspect ratio, duration and codec where applicable.
- Source, rights/consent and retention status.
- Checksum if generated by archive process.

### CONTINUATION_PROMPT.md
A clear instruction to continue from the last approved scene, preserve the attached Story Bible and references, not redesign canon characters/products/locations, respect screenplay and shot list, and generate only the specified next shots. Explicitly list what may and may not change.

## 7. Credit and cost controls

- Video, audio and 3D use credits; cost depends on model, resolution, duration and output count.
- Planning and default-quality images may use weekly free quota on eligible personal Go/Plus/Pro accounts; do not assume the same on Free, Team or Enterprise.
- Drafts do not charge until Run is pressed.
- Failed prompt-blocked generations may be refunded; completed generations that are low quality are not automatically refunded.
- Regeneration costs again; avoid vague prompts and repeated retries.
- Auto-select in AI Audio/Music may generate multiple versions and multiply cost.
- Check the live configuration estimate before every run; model prices and availability change.
- Maintain a project reserve for approved reshoots and audio.
- Never promise a fixed credit-to-minute ratio before pilot measurement.

## 8. Project naming and versioning

Recommended IDs:
- AVF-YYYY-NNN — film/series
- AVC-YYYY-NNN — campaign/ad
- AVS-YYYY-NNN — social content
- AVI-YYYY-NNN — image/brand kit
- AVX-YYYY-NNN — interactive/motion/3D

Version naming:
- v001 = first generated candidate.
- v002 = revised candidate.
- FINAL-APPROVED = customer-approved master.
- FINAL-DELIVERY = export delivered.

Do not overwrite source assets. Preserve approved versions and log replacements.

## 9. Security, privacy and rights

- Obtain written permission for likeness, voice, footage, logos, music and third-party assets.
- Do not upload confidential customer assets to external AI providers until customer authorization and provider terms are checked.
- Minimize personal data in prompts.
- Restrict R2 access and avoid public links for unreleased work.
- Do not use AI-generated testimonials or fake endorsements.
- Keep model/provider, generation date and rights notes with each deliverable.
- Respect platform synthetic-media disclosure rules where applicable.

## 10. Official references

- Media Studio: https://www.genspark.ai/helpcenter/media-studio
- Recipes: https://www.genspark.ai/helpcenter/media-studio-recipes
- Story, Assets & Collaboration: https://www.genspark.ai/helpcenter/media-studio-story-assets-and-sharing
- 3D & HTML Pages: https://www.genspark.ai/helpcenter/media-studio-3d-and-html
- Credits Guide: https://www.genspark.ai/helpcenter/credits-guide

Reviewed 2026-11-03. Re-check the live account and official documentation before committing scope, credits or deadlines.
