# EP01 production state — "Where Your Money Actually Goes"

Mode: **stills** (`picture-flow`) · Channel: Explainer · Style: **Stickman Cartoon**
(card `237dd06c-3729-4895-9672-1c623c4266e0`, donor media `969b14ca-6468-4a7e-af3c-3ba8028fd41f`)
Aspect **16:9** · Voice **Cillian** `d8ba9f14-8a24-44db-932b-99e16c45bd32` / `preset`

## Locked style formula (byte-identical in every prompt)

> flat 2D webcomic cartoon, extremely minimal — uniform thin even-weight black outlines,
> egg-shaped heads with tiny dot eyes and a single line mouth, plain noodle limbs, solid
> flat color fills with NO shading, NO gradients, NO texture, deadpan minimalist design,
> plain flat solid-color backgrounds.

PALETTE LOCK: warm cream paper background, near-black ink outlines, one emerald green
accent and one red accent — no other colors, no gradients, no painted or textured
backgrounds.

## DONE

**Style key** `029446ad-ad3e-4ae8-b875-433940306d89`

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

**Asset roster (17)** — all `seedream_v5_pro`, style key attached as `image_references`

| idx | asset | job id |
|---|---|---|
| 10 | MARV (2:3) | `d4cb674b-dc34-4f48-ad6f-f5a2b16f355b` |
| 11 | BARISTA (2:3) | `835a2a66-a8ed-4096-9f4c-249ad33ca3df` |
| 12 | SUIT (2:3) | `bfdc011b-3d1d-410b-80a0-c7374302b1a6` |
| 13 | FARMER (2:3) | `e7472cff-6319-41e0-8c86-059e53eb0ebd` |
| 14 | LANDLORD (2:3) | `b1a3db97-a896-4235-94e8-2a6dd08fae2e` |
| 20 | CAFE_COUNTER | `7918f8ad-da33-4f5b-8934-a37cc6d90ab8` |
| 21 | LEDGER_VOID | `9caa7143-b099-4f65-9595-9e7d662cd9ca` |
| 22 | RAILS | `942347eb-04ac-4b5d-8578-8f62d72c35cf` |
| 23 | BANK_LOBBY | `b4d4ff0e-5ee4-4ce5-9a4a-c857f5c19bbc` |
| 24 | NETWORK_TOWER | `d5ce481e-187e-40d5-958f-781d3e6c5d92` |
| 25 | COFFEE_FARM | `84bd5566-2cd8-4381-ae4c-b22de1860b1b` |
| 26 | PORT | `2c6ed3ea-0585-4ea4-9a67-0525a0744e9b` |
| 27 | LANDLORD_OFFICE | `e2a02262-0f86-4087-aead-0acdb9548aa0` |
| 28 | MARV_HOME | `4649c88b-c0c6-484a-8e1e-a8e404c33dd4` |
| 30 | THE_TWENTY (1:1) | `85f7aed6-638d-4d8e-9c21-05410afad479` |
| 31 | CARD_TERMINAL (1:1) | `18ec13d3-837a-445e-b649-c21a08c5e863` |
| 32 | COFFEE_CUP (1:1) | `64fea2cb-acbe-405d-9f68-b7d0ce82741b` |

## REMAINING

1. **Frames** — assembler floor is `ceil(376.86 / 1.5)` = **252**; target ~310.
   Roughly ⅓ KIND-A (new framing, composed from location → character → prop refs) and
   ⅔ KIND-B (edit of the previous frame's job_id as the ONLY ref, one visible change,
   never more than 2 in a row). `resolution: "1k"`, `aspect_ratio: "16:9"`.
   Name each `frameNNN.png` by **timeline number in spoken order**, never finish order.
2. **Assemble** — `assemble_slides.sh --audio narration.wav --blocks N`, manifest is
   `frameNNN.png <seconds>` ascending, durations `start(n+1) - start(n)` from Whisper.
3. **Subtitles** — subtitles skill, `clean` look.
4. **Topaz upscale** → deliver one `final.mp4`.

## Costs measured (correcting earlier estimates)

| Item | Credits |
|---|---|
| `seedream_v5_pro` @ 2k | ~6.7 |
| `seedream_v5_pro` @ 1k | **1.5** |
| `seed_audio` per chunk | ~0.1 |
| `gemini_omni` 10s block | 30 |

Spent so far: **87** (style key + 17 assets + 4 narration chunks). Balance **984**.
Frames at 1k ≈ 380–465. Projected total ≈ 500, leaving ~480.

## Gotchas hit

- Plus plan caps **8 concurrent image jobs**; over that the API returns
  `"Out of credits on plus (monthly) plan"`, which is misleading — it is a concurrency
  error. Throttle submissions to ≤8 in flight and resubmit failed indices.
- `sandbox_exec` with `background:true` failed at the transport layer twice; foreground
  with `timeout_seconds:120` works. The sandbox is discarded ~10s after each call, so
  every stage must re-download its inputs from the CDN URLs above.
- Whisper needs 16kHz mono input (`-ar 16000 -ac 1`) to run inside the 120s budget.
