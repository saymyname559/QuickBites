# QuickBites
Online Food ordering System Using PHP

posting Sql soon.

---

## Flutter Development Setup (Windows)

If you are contributing to or extending this project with Flutter, follow the steps below to resolve common `flutter doctor` issues on Windows.

### Prerequisites

- [Flutter SDK](https://docs.flutter.dev/get-started/install/windows) (stable channel)
- [VS Code](https://code.visualstudio.com/) ✅ (already installed)
- [Android Studio](https://developer.android.com/studio) — required for Android SDK and cmdline-tools

---

### Fix 1 — Android Toolchain: `cmdline-tools component is missing`

The Android SDK **command-line tools** must be installed separately.

**Option A — Android Studio (recommended):**

1. Open **Android Studio** → **SDK Manager** (via *More Actions* on the welcome screen, or *Tools → SDK Manager* inside a project).
2. Go to the **SDK Tools** tab.
3. Check **Android SDK Command-line Tools (latest)** and click **Apply / OK**.

**Option B — Manual download:**

1. Download the command-line tools from: <https://developer.android.com/studio#command-line-tools-only>
2. Extract the archive to `%LOCALAPPDATA%\Android\Sdk\cmdline-tools\latest\` so that `sdkmanager.bat` is located at:
   ```
   %LOCALAPPDATA%\Android\Sdk\cmdline-tools\latest\bin\sdkmanager.bat
   ```
3. Set (or confirm) the environment variable:
   ```
   ANDROID_HOME=%LOCALAPPDATA%\Android\Sdk
   ```
4. Add the following to your `PATH`:
   ```
   %ANDROID_HOME%\cmdline-tools\latest\bin
   %ANDROID_HOME%\platform-tools
   ```

After installing the tools, accept the Android SDK licenses:

```powershell
flutter doctor --android-licenses
```

Press `y` to accept each license.

---

### Fix 2 — Chrome: `Cannot find Chrome executable`

Flutter needs Google Chrome to run web apps.

**Option A — Install Chrome:**

Download and install Google Chrome from <https://www.google.com/chrome/>.

**Option B — Point Flutter to an existing Chromium-based browser:**

If you have a Chromium-based browser installed at a non-default path, set the `CHROME_EXECUTABLE` environment variable:

1. Open **System Properties** → **Advanced** → **Environment Variables**.
2. Under *User variables*, click **New** and add:
   - **Variable name:** `CHROME_EXECUTABLE`
   - **Variable value:** Full path to the browser executable, e.g.:
     ```
     C:\Program Files\Google\Chrome\Application\chrome.exe
     ```
3. Restart your terminal for the change to take effect.

---

### Fix 3 — Visual Studio: `Visual Studio not installed`

> **Note:** This is **Microsoft Visual Studio** (the full IDE for C++ development), which is **different from VS Code**. VS Code alone is not sufficient for building Flutter Windows desktop apps.

Flutter Windows desktop builds require the **Desktop development with C++** workload from Visual Studio.

1. Download **Visual Studio 2022 Community** (free) from: <https://visualstudio.microsoft.com/downloads/>
2. Run the installer.
3. On the *Workloads* screen, select **Desktop development with C++**.
4. Complete the installation.

If you do not need to build for Windows desktop and only target Android or web, you can safely ignore this warning.

---

### Verify your setup

After applying the fixes above, run:

```powershell
flutter doctor -v
```

All previously failing checks should now show a green ✓.
