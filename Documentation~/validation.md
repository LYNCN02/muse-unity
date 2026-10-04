# Validation status

Publication date: 2026-10-04. Public preview. Isolated standalone checks passed after publication; live-device acceptance remains incomplete.

## Passed for the extracted package

- macOS native source rebuilt as an arm64/x86_64 universal plugin; expected C ABI symbols verified.
- Android Java source compiled against an Android SDK; expected JNI methods verified.
- Selected-file extraction, explicit credential configuration, separate namespace/store identifiers, and pre-publication credential/private-dependency scan.
- Fresh Unity 6000.3.16f1 project: UPM installation, package compilation, TMP resource import, and the complete isolated C#/protocol/UI suite passed. See [test report](isolated-test-report.txt).
- Follow-up fixes: corrected managed crypto plugin importer metadata and guarded missing TMP settings during first import.
- Full Git-history and working-tree scan, including native binaries, found no credential-shaped literals or matches against private source-project credentials.

## Pending for the extracted package

- New account binding and credential restoration using the package's independent store.
- Complete live speech → Muse → visible Unity reply acceptance.
- Android device / IL2CPP / APK, macOS standalone, and multilingual font coverage.

## Source-implementation evidence (not standalone acceptance)

The original implementation passed isolated C# protocol/UI fixtures and had real iPad → Mac BLE authorization, encrypted credential saving, Muse connection and ElevenLabs transcription. A user saw the submitted message and reply in the Muse app. Unity reply handling was subsequently changed to use the existing main conversation, pre-subscribe and correlate canonical message IDs. Complete live Unity reply rendering has not yet been confirmed.

One Android 16 → macOS pairing attempt hit a phone-side GATT attribute size limit. That combination remains unsupported until revalidated. No physical-device claims are made from compilation or synthetic fixtures.
