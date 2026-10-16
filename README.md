# StageMic

**Mic plots, backstage handovers and live crew displays for theatre.**

StageMic helps you plan who wears each radio mic throughout a show, then gives your backstage team a live view of the changes they need to make. Run the control app on your computer and open the backstage display on an iPad, phone or laptop—no separate display app required.

This repository provides StageMic downloads and release notes. StageMic is proprietary software; its source code is not published here.

## Features

- **Mic, character and actor plots.** See allocations scene by scene, link characters to actors and handle actors playing multiple characters.
- **Faster plotting.** Fill allocations forward into blank scenes, rename and reorder scenes or characters, and highlight conflicting allocations.
- **Live backstage displays.** Show the current scene's handovers with actor names prominent, plus current mic allocations so crew can find the person wearing a particular pack.
- **Shared completion tracking.** Tick off handovers from backstage and see the same status on every connected display and in the control app.
- **QLab control.** Follow scene changes through OSC, with manual controls available in StageMic.
- **Show paperwork.** Print plots and swap lists, print individual actor reports, export actor and character plots as CSV, or copy tables into an email.
- **Local show files.** Save and load `.mic` files, with automatic saving of your current show.

## Download and install

Download the latest macOS build from this repository's [Releases](../../releases/latest) page, extract the archive and move **StageMic.app** into your Applications folder.

Open StageMic and activate it with your licence key. An internet connection is required for activation and any check-in required by your licence. Once activated, show control and backstage displays run locally within your offline licence allowance.

## Set up a show

1. Open **Production setup** and add your scenes, characters, actors and number of mics.
2. Assign characters to their actors where appropriate.
3. Use **Mic plot** to allocate characters to mics in each scene. Select **Mic table** for an explicit return to or collection from the table.
4. Review the character and actor plots, check any red conflict cells, and confirm the timing of the detected backstage swaps.
5. Use **Save** to keep a separate `.mic` show file. Autosave keeps your current work, but a saved show file is useful for backups and moving between computers.

## Connect backstage displays

Keep the controlling computer and display devices on a network that allows them to communicate. Open **Network setup**, then scan a display's QR code or copy its link into a browser. **Open** previews that display in the computer's default browser.

Two display links are available:

| Display | Mark completed | Undo completion |
| --- | --- | --- |
| Crew | Yes | Yes—brief Undo button, or hold a completed handover's button |
| Complete-only | Yes | No |

The control app can correct individual completion states in **Backstage swaps**. Use **Reset all completions** before the next performance.

Display links change when StageMic restarts. Reopen connected displays using the new links after a restart.

Wi-Fi and Ethernet can both be used. Guest networks with client isolation may prevent devices from connecting. Allow StageMic's incoming connections if your computer's firewall asks. Use a trusted backstage network; the display server is intended for local use.

## Control scenes from QLab

When QLab and StageMic run on the same Mac, the default OSC destination is:

- **Address:** `127.0.0.1`
- **UDP port:** `9000`

Create an OSC Network patch in QLab and send this message with **no arguments** to advance one scene:

```text
/stagemic/scene/go/next
```

You can also select a scene in StageMic and copy its individual OSC message from **Network setup**. Use these specific scene cues as reference points to resynchronise during the show.

Scene messages use stable scene identifiers, so renaming or reordering a scene preserves its individual cue address. Save the show before programming your cues, and test the opening scene and backstage displays before the performance.

## Optional completion alerts

In **Production setup**, enable **Alert me about handovers not marked complete** if your crew use completion tracking. This setting is off by default and is saved with the show.

When a scene change moves forward exactly one scene, StageMic checks the scene being left. If handovers remain unticked, it sends a silent computer notification and shows a dismissible warning inside the app. This applies to manual scene changes and OSC cues. Initial scene selection, repeated scenes, backward moves and jumps do not trigger alerts.

Scene control continues immediately. A warning means a handover was **not marked complete**; it does not prove the physical change was missed. OS notification permissions and Focus settings may affect whether a notification appears.

## Printing and sharing

Choose **Print** for formatted show paperwork. Select **Choose Actors** to print one page per selected actor; **Select all / Deselect all** applies to the whole actor list, including names hidden by a search. Use the system print dialog to print or save a PDF where available.

The actor and character plots also offer **Export CSV** and **Copy table** for sharing allocations. Completion ticks and green completion highlighting are not included in printed paperwork.

## Licensing

StageMic is proprietary software and requires a valid StageMic licence. Availability of downloads in this repository does not grant permission to redistribute, modify or relicense StageMic. Use is subject to the applicable StageMic licence terms.

Third-party components, including Electron, retain their respective licences. Their licence and copyright notices must be preserved with distributed builds.
