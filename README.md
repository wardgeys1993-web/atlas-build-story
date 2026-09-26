# Atlas: building a local AI companion alone

I started Atlas on 9 June 2026 because I wanted a useful voice assistant on my own Windows PC. I wanted it to remember context, work with files and speak back, with the model running on hardware I own. The first version came together quickly. Making it dependable has taken the rest of the journey.

Atlas is my solo project. I set the direction, made the product and technical decisions, implemented, tested and released it. I used AI coding tools, including Claude Code and Codex, in that workflow. They helped me move faster; I remained responsible for the design, failures and final calls.

**[Read the illustrated case study and watch the desktop demo](https://portfolio-pi-pearl-5yw08swac0.vercel.app/atlas.html#build-story)** · **[Android 0.12.0 release](https://github.com/wardgeys1993-web/atlas-companion-releases/releases/tag/v0.12.0)**

## The timeline

| When | What went wrong or changed | What I did |
| --- | --- | --- |
| 9 to 10 June | The early chat, memory, voice and tool loop raced across threads, lost streamed answers and could leave a model process behind. | Added lifecycle guards, thread-safe storage, regression tests, an offline network guard and an audit trail. |
| 11 to 15 June | Exploring a full desktop shell raised the risk of leaving a real PC at a blank screen. | Built a supervisor, boot failsafe and reversible shell path, with confirmation for risky actions. |
| 17 to 29 June | The interface flickered under load. My first guess was VRAM pressure. | Reduced repaint work, measured memory during the flicker and found events with more than 11 GiB free. That pushed the investigation toward the compositor and NVIDIA overlay. |
| 22 to 29 June | Model swaps on one 12 GB GPU could fail and leave Atlas without a brain. | Added VRAM checks, rollback and a smaller boot model. Later cache and attention work improved the context budget without changing the default 12B brain. |
| 7 to 13 July | Atlas sometimes said a desktop action was done after only sending a command. | Checked outcomes, added clearer approval and receipts, and made the response account for what really happened. |
| 11 to 20 July | The full shell was ambitious, but the floating companion fit everyday work better. | Moved the experience onto the normal Windows desktop and fixed oversized windows, clipped chat, voice echo and greeting loops. |
| August | A larger 26B model was tempting, but early runs had template and reply problems. | Repaired the experimental path and kept the proven 12B model as the default pending a fair comparison. |
| September | The Android client exposed TLS stalls, malformed tool schemas and a greeting that resumed an old task. | Traced the phone pipeline, repaired the connection and greeting paths, and published the 0.12.0 Android update. |

## Three lessons that changed the product

**Measure before fixing.** When the screen flickered, I could have kept shrinking the UI or model. A VRAM trace contradicted that simple explanation. The investigation was more useful once I treated the measurement as a reason to change direction.

**An action needs evidence.** A natural-language reply can sound complete when a tool only attempted a keystroke. Atlas now has guarded actions, confirmations, receipts and undo for reversible operations. The important check is the resulting file or system state, not the confidence of the sentence.

**A good form factor matters.** I built substantial shell work, then learned that a companion next to the apps I already use was easier to live with. The same local brain and trust layer could serve the simpler product. That pivot made daily use, not visual ambition, the test.

## Where it stands

The [portfolio demo](https://portfolio-pi-pearl-5yw08swac0.vercel.app/atlas.html#demo) shows a recorded August desktop workflow: Atlas speaks, handles a file request, and shows the result in Explorer. It is edited, labelled and captioned. It is evidence of that workflow, not a benchmark for the current build.

Android 0.12.0 has a [public release](https://github.com/wardgeys1993-web/atlas-companion-releases/releases/tag/v0.12.0). Newer alarm, timer and note work is being tested and still needs physical-phone validation. A new unedited desktop-to-phone demonstration is on my list. The local model runs on my Windows PC, and optional web and phone features have their own guarded network paths.

I am building Atlas because I want to work on practical software that survives real use. If that kind of engineering interests you, [my portfolio has the demo and contact details](https://portfolio-pi-pearl-5yw08swac0.vercel.app/).
