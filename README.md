Welcome to a new version of Russian ЯВЕРТЫ

A Windows keyboard layout for typing Russian using a phonetic (homophonic) mapping, where each
Latin key maps to the Cyrillic letter it sounds like (z → з, w → в, i → и, …).

It is built on top of the Swedish physical keyboard layout, so key positions,
punctuation, and AltGr characters line up with a Swedish keyboard.

Layout
See the attached mapping images for more information.
The mapping is homophonic — Latin key → phonetically similar Cyrillic letter. 

Installation

*Option A — Installer (easiest)*

Download the latest release and unzip it.
Run setup.exe.
Add the keyboard under Settings → Time & language → Language & region →
Russian → ⋯ → Language options → Add a keyboard, then select this layout.

To remove the built-in Russian — Mnemonic keyboard so it doesn't clutter your input
switcher, remove it from the same Language options screen.

*Option B — Build from source*

Requirements: Microsoft Keyboard Layout Creator 1.4 (MSKLC) and .NET Framework 3.5
enabled (Control Panel → Turn Windows features on or off).

Open src/<layout>.klc in MSKLC.
Project → Build DLL and Setup Package.
Run the generated setup.exe.

If the build fails, see the note below.

The MSKLC "spaces in the path" gotcha

If MSKLC fails to build and the log is nothing but:

    CL.EXE returned 1
    RC.EXE returned 1
    LINK.EXE returned 1

…it is not your layout — the compiler, resource compiler, and linker are all failing to
run. This is a long-standing MSKLC bug: it chokes on the spaces in its default install
path (C:\Program Files (x86)\Microsoft Keyboard Layout Creator 1.4\). Fix it by running
MSKLC from a space-free path:

Copy the entire MSKLC folder to a path with no spaces, e.g. C:\msklc14.
(From an admin PowerShell:
Copy-Item "C:\Program Files (x86)\Microsoft Keyboard Layout Creator 1.4" C:\msklc14 -Recurse)
Launch C:\msklc14\MSKLC.exe as administrator.
Keep your .klc and its working directory on a no-space, Latin-only path too
(e.g. C:\kbd\) — a Cyrillic username or a spaced Documents path triggers the same error.
Open the .klc, then Project → Build DLL and Setup Package.

Note: double-clicking a .klc file still opens the copy in Program Files, so always launch
MSKLC from C:\msklc14 until the build succeeds.

Notes & known limitations

Designed for a Swedish physical keyboard. On other physical layouts the letters still
type correctly, but the legends printed on non-letter keys may not match.

License

MIT — see LICENSE. Built from scratch with Microsoft Keyboard Layout Creator 1.4
(no third-party layout used as a base).

Credits


Mapping mirrors the ChromeOS / Linux ru(phonetic) phonetic layout.
Built with Microsoft Keyboard Layout Creator 1.4.
