# EP01 production state — "Where Your Money Actually Goes"

Mode: **stills** (`picture-flow`) · Channel: Explainer · Style: **Stickman Cartoon**
(card `237dd06c-3729-4895-9672-1c623c4266e0`, donor media `969b14ca-6468-4a7e-af3c-3ba8028fd41f`)
Aspect **16:9** · Voice **Cillian** `d8ba9f14-8a24-44db-932b-99e16c45bd32` / `preset`

## Locked style formula (byte-identical in every prompt)

> flat 2D webcomic cartoon, extremely minimal — uniform thin even-weight black outlines,
> egg-shaped heads with tiny dot eyes and a single line mouth, plain noodle limbs, solid
> flat color fills with NO shading, NO gradients, NO texture, deadpan minimalist design,
> plain flat solid-color backgrounds.

PALETTE LOCK (v2 — the ONLY one to use; v1 is dead, see below):

> warm cream paper and near-black ink dominate the frame; large surfaces are cream,
> off-white, muted warm grey and soft tan. Emerald green and red appear ONLY as small
> sparing accents on one or two meaningful details, never as large fills. No other
> saturated colors, no gradients, no painted or textured backgrounds.

Paste the style formula AND this palette lock, byte-identical, into every KIND-A prompt.
KIND-B prompts carry neither — they use only the edit sentence in §RESUME.

---

# RESUME HERE

**Next action: wave A, frames 121 onward.** Read `EP01-waveA-beats.tsv`, take the next 8
rows, submit them as one `generate_image_batch`, wait, append the returned job ids to
`EP01-frame-ledger.tsv`, repeat. 79 wave-A frames remain, then 235 KIND-B frames.

**KIND-A prompt shape** (`seedream_v5_pro`, `aspect_ratio:"16:9"`, `resolution:"1k"`,
`medias` = location → characters → props, all role `image_references`):

```
{SHOT}: {beat}. Staged fresh as a full dressed scene, matching the reference images for
location, character identity, colors and background. In THIS EXACT style: {STYLE FORMULA}
{PALETTE LOCK v2} No text, no watermark.
```

**KIND-B prompt shape** — the predecessor frame's job_id as the ONE and ONLY `medias`
entry. No asset sheets, no location, no props, no style formula, no palette lock; adding
any of them makes the model rebuild the scene instead of editing it:

```
Take the reference image and keep it EXACTLY: same composition, same crop, same camera,
same character, same colors, same background, same style. Change ONLY: {one visible
change}. Do not redraw or re-stage anything else.
```

Wave B1 = every frame where `(n-1)%3==1`, editing `n-1` (all parallel, different bases).
Wave B2 = every frame where `(n-1)%3==2`, editing `n-1`. Frames 2 and 3 are already done
and confirm the mechanism works — match their wording.

Each KIND-B change must be **visible at a glance**: an arm moves, the head turns, an
object enters or leaves. A raised eyebrow is invisible in one second of screen time.

## DONE

**Style key** `e9d4a449-02e7-4fed-873a-8c36d7a49e1a` (palette v2 — supersedes `029446ad…`)

**PALETTE LOCK v2** — the v1 lock said "one emerald green accent and one red accent",
which the model read as *use green and red everywhere*. Corrected to:

> warm cream paper and near-black ink dominate the frame; large surfaces are cream,
> off-white, muted warm grey and soft tan. Emerald green and red appear ONLY as small
> sparing accents on one or two meaningful details, never as large fills. No other
> saturated colors, no gradients, no painted or textured backgrounds.

Also removed green baked into individual asset prompts (barista's apron → warm grey,
coffee shrubs → muted sage), since those forced green into whole locations regardless
of the palette line.

**Asset roster v2 (17)** — all regenerated against the v2 style key

| idx | asset | job id |
|---|---|---|
| 10 | MARV (2:3) | `b05fadc6-2c33-4ff0-8869-6dbcd80cd82c` |
| 11 | BARISTA (2:3) | `2835193d-2b54-40f5-90fa-9ded780901d0` |
| 12 | SUIT (2:3) | `64880cdb-285f-481a-b3c7-b80f83853595` |
| 13 | FARMER (2:3) | `e3688e03-f642-4e25-a573-20302e6486d1` |
| 14 | LANDLORD (2:3) | `b3e753f7-af4d-407d-bed3-ac2985971c1a` |
| 20 | CAFE_COUNTER | `df835f15-4fd7-4a95-a761-576c5c4d4fda` |
| 21 | LEDGER_VOID | `3c96eb3d-622e-46b6-a4da-cef2e584e1bc` |
| 22 | RAILS | `9c74addc-a567-48bc-a4a5-f3535a5d4f72` |
| 23 | BANK_LOBBY | `860c79a0-7f49-44a7-9dd5-91217c7e959d` |
| 24 | NETWORK_TOWER | `07847821-8699-406c-963b-18fd3dec4035` |
| 25 | COFFEE_FARM | `5763638d-8100-4a30-8fe4-1121d52fb26f` |
| 26 | PORT | `0c05b4c5-84a8-4d12-a387-5893da8bac2b` |
| 27 | LANDLORD_OFFICE | `7cb7743d-36e4-4db1-b1db-5d3cfc03e2f0` |
| 28 | MARV_HOME | `1dc4aeab-0a20-42f4-9626-639fe7617e64` |
| 30 | THE_TWENTY (1:1) | `258a05bd-1526-4687-b078-fd88417d8f54` |
| 31 | CARD_TERMINAL (1:1) | `5ca7f8f9-7c45-4e23-8ce6-0867909e2913` |
| 32 | COFFEE_CUP (1:1) | `3cd3704c-ae7b-4413-9d1e-7cbe55fcfdf0` |

**Narration** — 4 chunks, joined = `narration.wav`, **376.86s (6:17)**, 871 words,
Whisper gives 392 caption groups (~0.96s each). Delivery cue used verbatim on every chunk:
`dry deadpan explainer, neutral accent, calm measured timbre, unhurried pace, starts speaking immediately`

| # | chunk job id |
|---|---|
| 1 | `782049a4-85a8-488b-9fdc-a91b267a42b6` (86.73s) |
| 2 | `7a783a20-673a-47d5-989d-95540cfb7730` (107.71s) |
| 3 | `7d4d07b7-764a-48a6-ad4f-80007b3fb36c` (105.64s) |
| 4 | `51b71ec6-011c-4a55-aaeb-7396bde82a61` (76.79s) |

Script: `channel/scripts/EP01-narration-450.txt`

## FRAME ARCHITECTURE (locked)

**356 frames**, durations summing to 376.87s, max hold 1.5s — built by grouping Whisper
captions to ≤1.45s and splitting anything longer. Regenerate identically by re-running
Whisper on the joined narration and applying that same grouping.

**Pattern:** frame `n` is KIND-A when `(n-1) % 3 == 0`, otherwise KIND-B editing `n-1`.
That gives **119 KIND-A** / **237 KIND-B**, never more than 2 edits in a row and never 2
new framings in a row — both caps the format enforces.

**This splits into THREE PARALLEL WAVES** rather than 237 sequential chained calls:

| Wave | Frames | Depends on | Count |
|---|---|---|---|
| A | `(n-1)%3==0` | assets only — fully parallel | 119 |
| B1 | `(n-1)%3==1` | its own A frame (different A each) — parallel | 119 |
| B2 | `(n-1)%3==2` | its own B1 frame — parallel | 118 |

Submit **8 per call** (Plus concurrency cap), `resolution:"1k"`, `aspect_ratio:"16:9"`.
KIND-B passes the predecessor's job_id as the ONLY ref — no asset sheets, no location, no
props, or the model rebuilds the scene instead of editing it.

Name each `frameNNN.png` by **timeline number in spoken order**, never finish order.

### Scene map — 42 scenes, frame ranges

`1-12 CAFE · 13-16 LEDGER · 17-25 CAFE · 26-32 LEDGER · 33-41 RAILS · 42-47 RAILS ·
48-55 BANK · 56-61 BANK · 62-71 BANK · 72-78 TOWER · 79-84 RAILS · 85-91 HOME ·
92-99 HOME · 100-108 BANK · 109-115 LEDGER · 116-124 CAFE · 125-127 CAFE · 128-138 FARM ·
139-143 FARM · 144-153 PORT · 154-161 CAFE · 162-171 LANDLORD · 172-182 LEDGER ·
183-190 CAFE · 191-199 LEDGER · 200-207 CAFE · 208-214 LEDGER · 215-226 CAFE ·
227-233 CAFE · 234-246 LEDGER · 247-252 LEDGER · 253-263 BANK · 264-267 BANK ·
268-275 HOME · 276-282 HOME · 283-293 TOWER · 294-304 HOME · 305-311 BANK ·
312-322 HOME · 323-334 CAFE · 335-345 HOME · 346-356 LEDGER`

### Wave A progress

Batch 1 (frames 1,4,7,10,13,16,19,22) regenerated on palette v2:
`9c29a182…` `8d46285f…` `f706d013…` `1c197494…` `5fcfd152…` `9e7d4cd0…` `4a47a310…` `e07eab35…`
The v1 renders of these eight are discarded.

## REMAINING

1. **Frames** — 79 wave-A (beats already authored in `EP01-waveA-beats.tsv`), then 235
   KIND-B edits. Append every job id to `EP01-frame-ledger.tsv` as it completes.
2. **Assemble** — in `sandbox_exec`: re-download the 4 narration chunks, concat to
   `narration.wav`, re-run Whisper, regroup to the same 356 segments, download every frame
   from the ledger as `frameNNN.png` **by ledger number, never by job finish order**, then
   `assemble_slides.sh --audio narration.wav --blocks 356` with a manifest of
   `frameNNN.png <seconds>` ascending, durations `start(n+1) - start(n)`.
   Before assembling, print the ledger as `NNN → the beat's first five words` and read it
   top to bottom, then spot-check frames at ~25% / 50% / 75% against what is being said at
   that timestamp.
3. **Subtitles** — subtitles skill, `clean` look. Never hand-time or hand-burn.
4. **Topaz upscale** → deliver one `final.mp4`.

## Costs measured (correcting earlier estimates)

| Item | Credits |
|---|---|
| `seedream_v5_pro` @ 2k | ~6.7 |
| `seedream_v5_pro` @ 1k | **1.5** |
| `seed_audio` per chunk | ~0.1 |
| `gemini_omni` 10s block | 30 |

Spent so far: **~300** (two style keys, 34 assets across two palette passes, 4 narration
chunks, 42 frames). Balance **~770**. The 314 remaining frames cost ~470 at 1k, leaving
~300 of headroom for retries and the upscale.

## Gotchas hit

- Plus plan caps **8 concurrent image jobs**; over that the API returns
  `"Out of credits on plus (monthly) plan"`, which is misleading — it is a concurrency
  error. Throttle submissions to ≤8 in flight and resubmit failed indices.
- `sandbox_exec` with `background:true` failed at the transport layer twice; foreground
  with `timeout_seconds:120` works. The sandbox is discarded ~10s after each call, so
  every stage must re-download its inputs from the CDN URLs above.
- Whisper needs 16kHz mono input (`-ar 16000 -ac 1`) to run inside the 120s budget.
