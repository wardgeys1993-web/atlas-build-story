# Atlas: from Jarvis to an operating layer and back

I started this solo project on 9 June 2026 in a folder called `jarvis`. I wanted my own Jarvis: a companion that could remember our conversations, work on my PC, help me write software on the go, watch things with me, make a shopping list and eventually handle everyday online tasks. Those were the ambitions, not a list of features I claimed to have shipped.

I set the direction, built and tested Atlas, and made the product decisions myself. Claude Code and Codex were coding tools in my workflow. They helped me move faster; I remained responsible for the design, mistakes and final calls.

**[Read the illustrated case study and watch the desktop demo](https://portfolio-pi-pearl-5yw08swac0.vercel.app/atlas.html#build-story)** · **[Android 0.12.0 release](https://github.com/wardgeys1993-web/atlas-companion-releases/releases/tag/v0.12.0)**

## The path

| When | The decision | What I built or learned |
| --- | --- | --- |
| 9 June | Make a local companion with memory, voice and the ability to help on my own computer. | The first chat, memory, vision, voice and tool loop made the Jarvis idea tangible. |
| 11 to 15 June | More autonomous PC actions kept meeting the sensible boundary around protected system files. I decided to explore an operating layer with AI at its centre. | A Windows shell prototype gained a desktop face, taskbar, file and window surfaces, and a recovery path. |
| June to July | The operating layer had to be safe to use on my everyday PC, and the local model had to share one 12 GB GPU. | I added confirmation for risky actions, audit and receipts, boot failsafes, model checks and rollback. The shell remained a prototype over Windows, not a replacement for Windows. |
| 11 to 20 July | Building an entire operating system was far bigger than the companion I originally wanted. | I returned to a smaller Atlas beside my normal apps, carrying the local brain, tools, memory and safety work forward. |
| Early phone work | I had no desktop microphone. | An older Android app served only as a phone microphone for Atlas. It was not the current Android companion. |
| September | Bring the companion itself to the phone. | I built a separate native Android client with chat, voice, pairing and approvals. Version 0.12.0 is public; newer phone actions and alarms still need physical-device checks. |

## What the detour taught me

**Autonomy changes the stakes.** The boundary around system files was a protection I valued. Building an operating layer did not make that risk disappear. It forced me to design approvals, an audit trail, receipts and recovery so the owner can see and control consequential actions.

**A prototype can teach without becoming the final product.** The shell over Windows was real work, with its own boot and recovery problems. It showed me the scale of an AI operating system. Returning to a companion was a deliberate product decision, not starting over.

**The same idea can cross devices.** The phone-as-mic app solved a hardware problem. The native Android client is a later, separate extension of the desktop companion. It aims to bring the same assistant with me rather than merely send microphone audio to the PC.

## Where it stands

The [portfolio demo](https://portfolio-pi-pearl-5yw08swac0.vercel.app/atlas.html#demo) shows an edited August desktop workflow with Atlas speaking and handling a file request. The current Desktop Companion and Android interface previews show public sample requests, not one uninterrupted phone-to-PC run.

Android 0.12.0 has a [public release](https://github.com/wardgeys1993-web/atlas-companion-releases/releases/tag/v0.12.0). Newer alarm, timer and note work still needs physical-phone validation. The local model runs on my Windows PC, with guarded network paths for optional web and phone features.

I am still building the companion I pictured when I named the folder `jarvis`. If the journey interests you, [my portfolio has the demo and contact details](https://portfolio-pi-pearl-5yw08swac0.vercel.app/).
