SCREEN-CLONE EDIT NOTE (live DWM)
Source: LorenzCK/OnTopReplica master (official); verified against paulodeleo v3.5.1 portable.
Mechanism verified (line refs from workspace/ontopreplica_quality_pass.md):
- ThumbnailPanel.SetThumbnailHandle (~line 208): DwmManager.Register binds one HWND to DWM thumbnail.
- MainForm.SetThumbnail (~line 305): takes WindowHandle + ThumbnailRegion.
- ThumbnailRegion / ClientToThumbnail (~line 475): source-relative region drawing.
- BaseWindowSeeker (~line 26): EnumWindows for window selection.
Edit: Add menu/action to clone full screen by passing WindowHandle(GetDesktopWindow())
to SetThumbnail(); region draw stays identical (relative to SourceSize).
Click-forwarding: only InjectFakeMouseClick (Thumbnail_CloneClick ~line 87); no clipboard/text logic.
Build: .NET 4.7 (TargetFrameworkVersion v4.7), requires WindowsFormsAero.dll (line 101-103 .csproj).
Portable .exe: build output + WindowsFormsAero.dll beside it. Installer: NSIS script.nsi in Installer/.
No fabricated .cs; this is the instruction; compile requires Windows + MSBuild.
