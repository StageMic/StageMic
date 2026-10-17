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

Download the latest build from this repository's [Releases](../../releases/latest) page, and follow the instructions below for your version.

### macOS
Extract the archive and move the .app file to your Applications folder. Open StageMic, allow it to run in System Settings, and enter your Mac's login password when prompted to allow StageMic to store licence files in Keychain.

### Windows
Extract the archive and run StageMic.exe. This app is not Authenticode signed and therefore requires you to click "More info -> Run anyway".

Once StageMic opens, activate it with your licence key. An internet connection is required for activation and any check-in required by your licence. Once activated, show control and backstage displays run locally within your offline licence allowance.

## Set up a show

1. Open **Production setup** and add your scenes, characters, actors and number of mics.
2. Assign characters to their actors where appropriate.
3. Use **Mic plot** to allocate characters to mics in each scene. Select **Mic table** for an explicit return to or collection from the table.
4. Review the character and actor plots, check any red conflict cells, and confirm the timing of the detected backstage swaps.
5. Use **Save** to keep a separate `.mic` show file. Autosave keeps your current work, but a saved show file is useful for backups and moving between computers.

## Show Files
`.mic` files are used by StageMic to save and backup your show. On macOS builds, StageMic will register itself as the handler for .mic files. Windows does not, and requires shows to be loaded from within the app.

## Connect backstage displays

Keep the controlling computer and display devices on a network that allows them to communicate. Open **Network setup**, then scan a display's QR code or copy its link into a browser. **Open** previews that display in the computer's default browser.

Two display links are available:

| Display | Mark completed | Undo completion |
| --- | --- | --- |
| Crew | Yes | Yes—brief Undo button, or hold a completed handover's button |
| Complete-only | Yes | No |

The control app can correct individual completion states in **Backstage swaps**. Use **Reset all completions** before the next performance.

Wi-Fi and Ethernet can both be used. Guest networks with client isolation may prevent devices from connecting. Allow StageMic's incoming connections if your computer's firewall asks. Use a trusted backstage network - not a network accessible to the public.
The network interface which the display links bind to is configurable (default is 0.0.0.0:8910).

## Control scenes over OSC

The default OSC destination is:

- **Address:** `127.0.0.1`
- **UDP port:** `9000`

The intended default OSC message is /stagemic/scene/go/next.

You can also select a scene in StageMic and copy its individual OSC message from **Network setup**. Use these specific scene cues as reference points to resynchronise during the show - we suggest at the top of a show, the interval, and halfway through each half of the show.

StageMic also supports receiving /stagemic/scene with an argument for the number of a scene. For example "/stagemic/scene 1" would trigger the first scene.

Scene messages use stable scene identifiers, so renaming or reordering a scene preserves its individual cue address (though ".../scene 16" would not be preserved if a scene is added before it - we recommend using the IDs rather than numbers). Save the show before programming your cues, and test the opening scene and backstage displays before the performance.

## Optional completion alerts

In **Production setup**, enable **Alert me about handovers not marked complete** if your crew use completion tracking. This setting is off by default and is saved with the show.

When a scene change moves forward one scene, StageMic checks the scene being left. If handovers remain unticked, it sends a silent computer notification and shows a dismissible warning inside the app. This applies to manual scene changes and OSC cues. Initial scene selection, repeated scenes, backward moves and jumps do not trigger alerts.

Scene control continues immediately. A warning means a handover was **not marked complete**; it does not prove the physical change was missed. OS notification permissions and Focus settings may affect whether a notification appears.

We highly recommend allowing StageMic to break through Do Not Disturb, check your OS instructions on how to do this.

## Printing and sharing

Choose **Print** for formatted show paperwork. Select **Choose Actors** to print one page per selected actor; **Select all / Deselect all** applies to the whole actor list, including names hidden by a search. Use the system print dialog to print or save a PDF where available.

The actor and character plots also offer **Export CSV** and **Copy table** for sharing allocations. 

## Licensing

StageMic is proprietary software and requires a valid StageMic licence. Availability of downloads in this repository does not grant permission to redistribute, modify or relicense StageMic. Use is subject to the applicable StageMic licence terms.

**Licence keys are currently available on request only.**

Third-party components, including Electron, retain their respective licences. Their licence and copyright notices must be preserved with distributed builds.


## AI Use Disclaimer

StageMic was built by a solo developer with help from AI Agents. We want to be upfront about that, and honest about how AI has been used. 

The idea of StageMic, all its features, and the majority of the codebase are human-created. AI was used for the UI design, as we do not have a designer on the team. Additionally, some features were coded by AI. However, all AI-generated code has been checked by a human before even being executed.

Its direction and development are guided by practical theatre experience and testing on real shows. StageMic was created because we needed it for a show. 

### Privacy
We know that the use of AI in software can raise privacy concerns. 

Your show files and autosaved work are stored locally on your computer. When you connect backstage displays, StageMic shares live show information directly with those devices over your local network, never the internet.

StageMic does not upload your show data or usage analytics to us or to an AI provider.

An internet connection is required for licence activation and any required check-ins through Keygen.sh. Other licence-management actions, such as manual check-ins and deactivation, also contact Keygen. Show planning, OSC control and backstage displays otherwise run locally within your licence’s offline allowance.
