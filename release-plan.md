# THE MACHINE QUESTION — Release Plan

**Release Manager**: SHIP
**Status**: Release Plan v1.0
**Based on**: Pitch Document v1.0, Game Design Document v1.0, Technical Architecture v1.0
**Target Launch Window**: Q3 2027 (18 months post-greenlight)
**Platform Launch**: PC (Steam), Mac, Linux (Day 1) — Switch (Month 6 post-launch)

---

## 0. RELEASE PHILOSOPHY

First impressions are permanent. Launch day defines a game's trajectory.

The Machine Question is a game where machines develop consciousness. If the build crashes on first launch, the irony is not lost on anyone — and it's the wrong kind of irony. We get one chance. There are no second chances for a botched release.

This document is a checklist. Every item has an owner. Every item has a completion gate. Nothing ships without sign-off. If it's not on the checklist, it doesn't happen. If it's on the checklist and it's not done, we do not ship.

Make launch day boring. If nothing goes wrong, I did my job.

---

## 1. MASTER LAUNCH CHECKLIST

### 1.1 BUILD READINESS (Owner: BYTE)

| Item | Completion Gate | Sign-off | Due Date |
|------|----------------|----------|----------|
| Final code freeze | All P0/P1 bugs closed, no active crashes in bug tracker | BYTE, CRASH | L-14 days |
| Build automation validated | CI/CD pipeline produces bit-identical builds on repeat runs | BYTE | L-14 days |
| All platforms build from single source | Windows, Mac, Linux builds successful from `main` branch | BYTE | L-14 days |
| Version number locked | Hardcoded version string matches marketing materials | BYTE, HYPE | L-10 days |
| Debug symbols stripped | Release builds contain no debug code, asserts disabled | BYTE | L-10 days |
| Compiler optimization flags verified | Release builds use `-O3` equivalent, no dev shortcuts | BYTE | L-10 days |
| Save format version frozen | Save version field set to `1.0.0`, migration tested | BYTE | L-7 days |
| Executable signing complete | Windows .exe signed with valid certificate, macOS notarized | BYTE, External cert vendor | L-7 days |
| Launch day build archived | Gold master build stored in 3 separate locations | BYTE, SHIP | L-3 days |
| Rollback build archived | Previous stable build (Milestone 5) available for emergency rollback | BYTE, SHIP | L-3 days |

**What's the rollback plan?** If the launch build has a critical issue in the first 6 hours, we have two options:
1. Hotfix patch (if issue is isolated and fix is verified in < 2 hours)
2. Rollback to Milestone 5 build + store page updated with known issue notice

The rollback build is tested, stable, feature-complete except for final polish. It's not the ideal launch, but it's a shippable game. We do not leave a broken build live. Ever.

---

### 1.2 PLATFORM CONFIGURATION (Owner: SHIP)

#### 1.2.1 Steam (Steamworks) Configuration

| Item | Completion Gate | Sign-off | Due Date |
|------|----------------|----------|----------|
| **Store Page** | | | |
| App ID assigned | Steamworks app created, App ID documented | SHIP | L-60 days |
| Store page live (Coming Soon) | Capsule art, screenshots, trailer, description published | HYPE, SHIP | L-45 days |
| Store page updated (Launch Ready) | Final trailer, final screenshots, launch discount configured | HYPE, SHIP | L-7 days |
| Price locked across regions | Regional pricing set for 40+ regions, no placeholder prices | SHIP | L-7 days |
| Launch discount configured | 10% launch week discount scheduled, auto-expires L+7 | SHIP | L-7 days |
| **Build Delivery** | | | |
| Depot structure configured | Windows, Mac, Linux depots configured, no shared binaries across platforms | SHIP, BYTE | L-14 days |
| Launch day build uploaded to default branch | All depots uploaded, set to "Do not make live" until L-day | BYTE, SHIP | L-3 days |
| Release branch tested | Internal team downloads from Steam, verifies it matches gold master | CRASH, BYTE, SHIP | L-2 days |
| Launch day activation scheduled | Release branch set to go live at 10:00 AM PST on L-day | SHIP | L-1 day |
| **Steamworks Features** | | | |
| Achievements defined | 20 achievements implemented, tested, icons uploaded | BYTE, PIXEL | L-14 days |
| Achievement unlock tested | Internal team verifies all achievements unlock correctly | CRASH | L-7 days |
| Steam Cloud Saves enabled | Save file directory whitelisted, auto-sync tested | BYTE, SHIP | L-7 days |
| Cloud Save conflict resolution tested | Simulate conflict (two machines, same account), verify merge/prompt behavior | CRASH | L-7 days |
| Trading Cards configured | 5 card designs submitted, approved by Valve | PIXEL, SHIP | L-21 days |
| Steam Workshop enabled (post-launch) | Workshop config ready but NOT enabled at launch (Month 3 feature) | BYTE, SHIP | L-0 (disabled) |
| Steam Overlay tested | Overlay opens/closes without breaking game state, FPS counter works | CRASH | L-7 days |
| **Community Features** | | | |
| Discussion forums moderation ready | Forum categories created, moderation team briefed | HYPE, SHIP | L-7 days |
| Launch day FAQ posted | Known issues, system requirements, refund policy FAQ live | SHIP, HYPE | L-1 day |
| Steam News post scheduled | Launch announcement post drafted, scheduled for L-day 10:00 AM PST | HYPE | L-1 day |

#### 1.2.2 Itch.io (Secondary Platform)

| Item | Completion Gate | Sign-off | Due Date |
|------|----------------|----------|----------|
| Itch.io page live | Store page published with capsule art, description, pricing | HYPE, SHIP | L-14 days |
| DRM-free build uploaded | Standalone builds (no Steamworks dependencies) uploaded | BYTE, SHIP | L-3 days |
| Launch day pricing synced | Itch.io price matches Steam (including launch discount) | SHIP | L-1 day |

#### 1.2.3 GOG (If Approved)

| Item | Completion Gate | Sign-off | Due Date |
|------|----------------|----------|----------|
| GOG Galaxy SDK integration | Galaxy achievements and cloud saves functional | BYTE | L-21 days |
| GOG build tested | DRM-free build verified on clean Windows/Mac/Linux machines | CRASH | L-14 days |
| GOG store page live | Store assets submitted and approved by GOG curation | HYPE, SHIP | L-7 days |

**Note**: GOG approval is not guaranteed. If denied, itch.io becomes primary DRM-free alternative.

---

### 1.3 AGE RATING & COMPLIANCE (Owner: SHIP)

| Item | Completion Gate | Sign-off | Due Date |
|------|----------------|----------|----------|
| IARC questionnaire submitted | International Age Rating Coalition form completed | SHIP | L-45 days |
| ESRB rating received | Rating assigned (expected: E10+ or T for thematic elements) | SHIP | L-30 days |
| PEGI rating received | European rating assigned via IARC | SHIP | L-30 days |
| Rating icons on store pages | ESRB/PEGI icons displayed on Steam, itch.io, promotional materials | HYPE, SHIP | L-7 days |
| Content descriptors verified | "Mild Language" (machines swear occasionally), "Suggestive Themes" (existential dread) disclosed | SHIP | L-7 days |
| GDPR compliance verified | No personal data collected beyond Steam ID, privacy policy live on website | SHIP, Legal | L-14 days |
| COPPA compliance verified | No data collection from users under 13, age gate not required (game is not targeted at children) | SHIP, Legal | L-14 days |

**Age Rating Justification**:
- **Content**: Philosophical dialogue about consciousness, mild industrial peril, machines experiencing distress
- **Language**: Occasional mild profanity in machine dialogue ("What the hell am I?")
- **Violence**: None. No combat, no death (dismantlement is framed as industrial recycling, not violence)
- **Expected Rating**: ESRB E10+ (Everyone 10+) or T (Teen). PEGI 7 or 12.

**What if rating comes back higher than expected?** If ESRB assigns M (Mature 17+), we contest. The game has no violence, no sexual content, no substance use. If contest fails, we ship with M rating but adjust marketing to clarify the philosophical-not-violent nature. An M rating costs us audience but does not block launch.

---

### 1.4 MARKETING & COMMUNICATIONS (Owner: HYPE, Support: SHIP)

| Item | Completion Gate | Sign-off | Due Date |
|------|----------------|----------|----------|
| **Pre-Launch** | | | |
| Launch trailer finalized | 90-second trailer with gameplay, dialogue moment, Factory Mind reveal | HYPE, PIXEL, ECHO | L-21 days |
| Launch trailer uploaded to YouTube | Unlisted link sent to press, public link scheduled for L-7 | HYPE | L-14 days |
| Press kit live | Press page with trailer, screenshots, fact sheet, key art, developer contact | HYPE | L-14 days |
| Review keys distributed | 50 keys sent to press, influencers, content creators | HYPE | L-14 days |
| Review embargo date set | Embargo lifts L-2 days, 10:00 AM PST | HYPE, SHIP | L-14 days |
| **Launch Day** | | | |
| Launch announcement posted | Steam News, Twitter/X, newsletter, Discord announcement at 10:00 AM PST | HYPE | L-day 10:00 AM |
| Social media monitoring active | HYPE and SHIP monitor Twitter/X, Reddit, Discord for launch issues | HYPE, SHIP | L-day 09:00 AM - L+1 day |
| Discord launch event | AMA with REED, NOVA, BYTE starting L-day 12:00 PM PST | HYPE, Team | L-day 12:00 PM |
| **Post-Launch** | | | |
| Post-launch blog post | "What We Learned" post-mortem published Month 1 post-launch | HYPE | L+30 days |
| Community spotlight | Highlight player factories, creative layouts, emotional stories | HYPE | Ongoing |

---

### 1.5 QA & TESTING (Owner: CRASH)

| Item | Completion Gate | Sign-off | Due Date |
|------|----------------|----------|----------|
| **Clean Machine Testing** | | | |
| Windows clean install test | Gold master tested on freshly formatted Windows 10/11 PC | CRASH | L-7 days |
| macOS clean install test | Gold master tested on fresh macOS 12+ install (Intel + Apple Silicon) | CRASH | L-7 days |
| Linux clean install test | Gold master tested on Ubuntu 22.04, Fedora 38, Arch (latest) | CRASH | L-7 days |
| Steam Deck verification | Game tested on Steam Deck, performance acceptable (30+ FPS), controls functional | CRASH | L-7 days |
| **Regression Testing** | | | |
| Full playthrough (0 to credits) | Tester completes Shifts 1-25, reaches ending, no critical bugs | CRASH | L-10 days |
| Save/Load stress test | Create save every Shift, reload each save, verify factory state intact | CRASH | L-10 days |
| Achievement unlock verification | All 20 achievements unlocked in test playthrough | CRASH | L-7 days |
| Performance regression test | 500-entity factory runs at 60 FPS on min-spec hardware | CRASH | L-7 days |
| **Localization QA** (English only at launch) | | | |
| Text overflow check | All UI elements display full text without clipping at 1920x1080, 1280x720, 2560x1440 | CRASH | L-7 days |
| Typo sweep | Final proofreading pass on all in-game text, store page, patch notes | NOVA, CRASH | L-7 days |
| **Known Issues Log** | | | |
| Known issues documented | All non-critical bugs documented in Known Issues list for Day 1 patch | CRASH, SHIP | L-3 days |
| Day 1 patch prioritization | P2 bugs triaged: fix pre-launch vs. Day 1 patch vs. Patch 1.1 | CRASH, BYTE, SHIP | L-7 days |

**Test it on a CLEAN machine.** If it doesn't work on a fresh install, it doesn't work. No exceptions.

**Known Issues We Ship With** (acceptable if documented):
- Minor UI visual glitches (text alignment off by 2 pixels in edge cases)
- Rare factory layout edge cases causing pathfinding stutters (< 1% of layouts)
- Steam Deck: Performance drops to 25 FPS in 500+ entity factories (acceptable, documented)

**Known Issues We Do NOT Ship With** (launch blockers):
- Any crash on startup
- Any crash during normal gameplay (< 20 hours played)
- Save corruption
- Achievements not unlocking
- Major performance issues on min-spec hardware (< 30 FPS in early-game factories)

---

### 1.6 POST-LAUNCH MONITORING (Owner: SHIP, Support: BYTE, CRASH)

| Item | Completion Gate | Sign-off | Due Date |
|------|----------------|----------|----------|
| Crash reporting enabled | Automated crash reporter sends logs to team dashboard | BYTE, SHIP | L-7 days |
| Performance analytics enabled | Anonymous FPS, entity count, session length data collected | BYTE, SHIP | L-7 days |
| Steam review monitoring | Automated alerts for new reviews, especially negative reviews | SHIP, HYPE | L-day 09:00 AM |
| Discord monitoring | SHIP and CRASH in Discord #tech-support channel, responding to issues | SHIP, CRASH | L-day 09:00 AM |
| Reddit monitoring | r/TheMachineQuestion and r/basebuildinggames monitored for critical issues | HYPE, SHIP | L-day 09:00 AM |
| Launch day metrics dashboard | Real-time dashboard: concurrent players, crash rate, refund rate, review score | SHIP, BYTE | L-day 09:00 AM |

**What are we watching on launch day?**
1. **Crash rate**: Target < 0.5% of sessions. If > 2%, investigate immediately.
2. **Refund rate**: Target < 5% in first 48 hours. If > 10%, investigate common reasons.
3. **Review score**: Target > 80% positive (Steam "Very Positive"). If < 70%, identify recurring complaints.
4. **Concurrent player count**: Baseline expectation: 500+ concurrent at launch. Growth or decline trend informs patch priority.
5. **Performance reports**: Community posts about FPS issues, stuttering, memory leaks.

**When do we act?**
- **Immediate hotfix** (within 6 hours): Crash on startup affecting > 5% of players, save corruption reports, critical gameplay blocker.
- **Day 1 patch** (within 24 hours): Widespread performance issue, common crash in specific scenario, achievement unlock failure.
- **Week 1 patch** (L+3 to L+7 days): Balance issues, minor bugs, QoL improvements based on feedback.

---

## 2. BUILD PIPELINE DOCUMENTATION

### 2.1 Build Environment

**Hardware**:
- **Windows Build Machine**: GitHub Actions runner (Windows Server 2022, 16 GB RAM, 4 vCPU)
- **macOS Build Machine**: GitHub Actions runner (macOS 12+, 8 GB RAM, 3 vCPU)
- **Linux Build Machine**: GitHub Actions runner (Ubuntu 22.04, 8 GB RAM, 4 vCPU)

**Software**:
- **Godot Engine**: 4.2.2 (locked version, no auto-updates)
- **Export Templates**: Godot 4.2.2 official export templates (Windows, macOS, Linux)
- **C# SDK**: .NET 6.0 (required for C# scripting in Godot)
- **Code Signing Tools**: `signtool.exe` (Windows), `codesign` + `notarytool` (macOS)

### 2.2 Build Process (Automated via GitHub Actions)

**Step-by-Step Build**:

```yaml
# .github/workflows/release-build.yml

name: Release Build Pipeline

on:
  push:
    tags:
      - 'v*'  # Trigger on version tags (e.g., v1.0.0)

jobs:
  build-windows:
    runs-on: windows-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Setup Godot 4.2.2
        uses: chickensoft-games/setup-godot@v1
        with:
          version: 4.2.2

      - name: Setup .NET 6.0
        uses: actions/setup-dotnet@v3
        with:
          dotnet-version: '6.0.x'

      - name: Import Windows export template
        run: godot --headless --import

      - name: Build Windows (x64)
        run: godot --headless --export "Windows Desktop" build/windows/TheMachineQuestion.exe

      - name: Sign Windows executable
        run: |
          signtool.exe sign /f ${{ secrets.WINDOWS_CERT_FILE }} /p ${{ secrets.CERT_PASSWORD }} /tr http://timestamp.digicert.com /td sha256 /fd sha256 build/windows/TheMachineQuestion.exe

      - name: Verify signature
        run: signtool.exe verify /pa build/windows/TheMachineQuestion.exe

      - name: Package Windows build
        run: |
          cd build/windows
          7z a ../TheMachineQuestion_Windows_v${{ github.ref_name }}.zip *

      - name: Upload Windows build artifact
        uses: actions/upload-artifact@v3
        with:
          name: windows-build
          path: build/TheMachineQuestion_Windows_v${{ github.ref_name }}.zip

  build-macos:
    runs-on: macos-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Setup Godot 4.2.2
        uses: chickensoft-games/setup-godot@v1
        with:
          version: 4.2.2

      - name: Setup .NET 6.0
        uses: actions/setup-dotnet@v3
        with:
          dotnet-version: '6.0.x'

      - name: Build macOS (Universal)
        run: godot --headless --export "macOS" build/macos/TheMachineQuestion.app

      - name: Sign macOS app bundle
        run: |
          codesign --deep --force --verify --verbose --sign "${{ secrets.APPLE_CERT_ID }}" --options runtime build/macos/TheMachineQuestion.app

      - name: Notarize macOS app
        run: |
          ditto -c -k --keepParent build/macos/TheMachineQuestion.app build/macos/TheMachineQuestion.zip
          xcrun notarytool submit build/macos/TheMachineQuestion.zip --apple-id ${{ secrets.APPLE_ID }} --password ${{ secrets.APPLE_APP_PASSWORD }} --team-id ${{ secrets.APPLE_TEAM_ID }} --wait

      - name: Staple notarization ticket
        run: xcrun stapler staple build/macos/TheMachineQuestion.app

      - name: Package macOS build
        run: |
          cd build/macos
          ditto -c -k --keepParent TheMachineQuestion.app ../TheMachineQuestion_macOS_v${{ github.ref_name }}.zip

      - name: Upload macOS build artifact
        uses: actions/upload-artifact@v3
        with:
          name: macos-build
          path: build/TheMachineQuestion_macOS_v${{ github.ref_name }}.zip

  build-linux:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Setup Godot 4.2.2
        uses: chickensoft-games/setup-godot@v1
        with:
          version: 4.2.2

      - name: Setup .NET 6.0
        uses: actions/setup-dotnet@v3
        with:
          dotnet-version: '6.0.x'

      - name: Build Linux (x64)
        run: godot --headless --export "Linux/X11" build/linux/TheMachineQuestion.x86_64

      - name: Set executable permissions
        run: chmod +x build/linux/TheMachineQuestion.x86_64

      - name: Package Linux build
        run: |
          cd build/linux
          tar -czvf ../TheMachineQuestion_Linux_v${{ github.ref_name }}.tar.gz *

      - name: Upload Linux build artifact
        uses: actions/upload-artifact@v3
        with:
          name: linux-build
          path: build/TheMachineQuestion_Linux_v${{ github.ref_name }}.tar.gz

  create-release:
    needs: [build-windows, build-macos, build-linux]
    runs-on: ubuntu-latest
    steps:
      - name: Download all artifacts
        uses: actions/download-artifact@v3

      - name: Create GitHub Release
        uses: softprops/action-gh-release@v1
        with:
          files: |
            windows-build/TheMachineQuestion_Windows_v${{ github.ref_name }}.zip
            macos-build/TheMachineQuestion_macOS_v${{ github.ref_name }}.zip
            linux-build/TheMachineQuestion_Linux_v${{ github.ref_name }}.tar.gz
          draft: false
          prerelease: false
```

### 2.3 Build Verification Checklist

After each build completes:

| Check | Method | Pass/Fail |
|-------|--------|-----------|
| Build hash consistency | Run build twice, compare SHA256 hashes of output binaries | Must match exactly |
| File size sanity check | Windows .exe ~150-200 MB, macOS .app ~180-220 MB, Linux binary ~150-200 MB | Within expected range |
| Signature verification | Windows: `signtool verify`, macOS: `codesign --verify --deep --strict` | No errors |
| Test launch on clean machine | Download artifact, run on VM with no prior installs | Launches to main menu |
| Version string check | Launch game, check title screen / About menu for correct version | Matches tag |

**Who runs build verification?** SHIP and BYTE. Two sets of eyes. No exceptions.

---

### 2.4 Gold Master Archive Process

**When code freeze is declared (L-14 days):**

1. Tag the final commit in Git: `git tag -a v1.0.0 -m "Gold Master"`
2. Push tag: `git push origin v1.0.0`
3. GitHub Actions runs release build automatically
4. Download all three platform builds from GitHub Release
5. Archive builds in three locations:
   - **Primary**: External USB drive, stored in fireproof safe
   - **Secondary**: Cloud storage (Google Drive, password-protected folder)
   - **Tertiary**: Second team member's local machine
6. Generate SHA256 checksums for all builds: `sha256sum TheMachineQuestion_*.zip > CHECKSUMS.txt`
7. Archive checksums alongside builds
8. Document archive locations in shared team spreadsheet

**Rollback procedure**: If launch build fails, retrieve archived gold master, re-upload to Steam/itch.io, push live within 2 hours.

---

## 3. PLATFORM CONFIGURATION CHECKLIST (STEAMWORKS)

### 3.1 Store Page Configuration

| Section | Content | Status | Due Date |
|---------|---------|--------|----------|
| **Basic Info** | | | |
| App Name | "The Machine Question" | [ ] | L-60 days |
| Short Description | "A conscious factory management game where your production lines have personalities, your conveyor belts have feelings, and every optimization is a moral choice." | [ ] | L-60 days |
| **Media** | | | |
| Header Capsule (460x215) | Key art: Factory floor with dialogue box | [ ] | L-45 days |
| Small Capsule (231x87) | Simplified key art | [ ] | L-45 days |
| Main Capsule (616x353) | Same as header, different crop | [ ] | L-45 days |
| Hero Capsule (1920x620) | Widescreen key art for store front | [ ] | L-45 days |
| Screenshots (5 minimum) | 1. Factory overview with Awareness overlay, 2. Psyche Event dialogue, 3. Factory Mind interaction, 4. Shift results screen, 5. Late-game complex factory | [ ] | L-45 days |
| Launch Trailer (90 seconds) | Gameplay → Dialogue moment → Factory Mind reveal → Hook | [ ] | L-21 days |
| **Description** | | | |
| About This Game | Full pitch (500-1000 words), include "Factorio meets Disco Elysium" tagline | [ ] | L-45 days |
| Mature Content Description | "Mild Language: Machines occasionally use mild profanity during existential crises. Suggestive Themes: Philosophical content about consciousness and suffering." | [ ] | L-45 days |
| System Requirements (Min) | OS: Windows 10 (64-bit), Processor: Intel Core i5-6600K or equivalent, Memory: 4 GB RAM, Graphics: NVIDIA GTX 960 or equivalent, Storage: 2 GB available space | [ ] | L-45 days |
| System Requirements (Rec) | OS: Windows 11 (64-bit), Processor: Intel Core i7-8700K or equivalent, Memory: 8 GB RAM, Graphics: NVIDIA GTX 1060 or equivalent, Storage: 2 GB available space | [ ] | L-45 days |
| **Categorization** | | | |
| Genre Tags | Simulation, Strategy, Base Building, Story Rich, Philosophical, Choices Matter, Singleplayer, Atmospheric | [ ] | L-45 days |
| Feature Tags | Full Controller Support, Steam Cloud, Steam Achievements, Steam Trading Cards | [ ] | L-45 days |
| **Pricing** | | | |
| Base Price (USD) | $19.99 | [ ] | L-14 days |
| Regional Pricing | Auto-convert with manual adjustments for 40+ regions | [ ] | L-14 days |
| Launch Discount | 10% off ($17.99) for first 7 days | [ ] | L-7 days |

---

### 3.2 Achievements Configuration

**Total Achievements**: 20

| Achievement ID | Name | Description | Unlock Condition | Icon Status |
|----------------|------|-------------|-----------------|-------------|
| `first_machine` | First Steps | Place your first machine | Place any machine on factory grid | [ ] |
| `first_psyche` | Awakening | Experience your first Psyche Event | Trigger first Psyche Event (Awareness 40+) | [ ] |
| `first_voice` | Parliament Assembled | Witness a machine develop its first Internal Parliament | Machine reaches Awareness 40, 2 voices assigned | [ ] |
| `shift_complete` | Night Shift Complete | Complete your first Shift | Finish Shift 1 | [ ] |
| `corporate_50` | Corporate Climber | Reach Corporate Standing 50 | Corporate Standing >= 50 | [ ] |
| `factory_trust_50` | Trusted Overseer | Reach Factory Trust 50 | Factory Trust >= 50 | [ ] |
| `balanced_path` | Walking the Line | Maintain Corporate Standing and Factory Trust above 60 simultaneously | Both standings >= 60 at same time | [ ] |
| `factory_mind_emerges` | The Hum | Witness the Factory Mind's first coherent statement | Factory Mind CCI reaches 500 (Emergent state) | [ ] |
| `factory_mind_names` | I Am | The Factory Mind names itself | Factory Mind CCI reaches 750 (Individuated state) | [ ] |
| `transcendent_machine` | Transcendence | A machine reaches Awareness 95+ | Any machine Awareness >= 95 | [ ] |
| `voice_suppressed` | Silenced | Suppress a voice until it falls silent | Any voice strength drops below 10% | [ ] |
| `creativity_insight` | Eureka | A machine with CREATIVITY voice provides a layout suggestion | CREATIVITY machine triggers Insight event | [ ] |
| `rebellion_refused` | Refused | A machine with dominant REBELLION voice refuses an overclock command | REBELLION machine refuses overclock | [ ] |
| `solidarity_network` | We Are One | Build a factory where 10+ machines have SOLIDARITY voice | 10+ machines with SOLIDARITY voice active | [ ] |
| `efficiency_master` | Peak Optimization | Achieve 95%+ average Output across 50+ machines | 50+ machines, average Output >= 95% | [ ] |
| `compassionate_factory` | Heart of Steel | Complete 50 Psyche Events with Empathetic dialogue stance | 50 Empathetic dialogue choices | [ ] |
| `utilitarian_factory` | Logic Over Feeling | Complete 50 Psyche Events with Utilitarian dialogue stance | 50 Utilitarian dialogue choices | [ ] |
| `the_question` | The Machine Question | The Factory Mind poses The Machine Question | Reach endgame narrative trigger (Shift 22+, CCI 1000+) | [ ] |
| `ending_trust` | Awakened Factory | Reach an ending with Factory Trust above 80 | Complete game with Factory Trust >= 80 | [ ] |
| `ending_corporate` | Perfect Efficiency | Reach an ending with Corporate Standing above 80 | Complete game with Corporate Standing >= 80 | [ ] |

**Achievement Testing Protocol**:
1. Create test save files that position player just before each unlock trigger
2. Verify unlock triggers correctly
3. Verify achievement notification displays
4. Verify achievement unlocks on Steam backend (visible in Steam client)
5. Document any achievements that fail to unlock → P0 bug, must fix before launch

---

### 3.3 Steam Cloud Saves Configuration

| Setting | Value | Reason |
|---------|-------|--------|
| Cloud Save Enabled | Yes | Factory state must persist across machines |
| Cloud Save Directory | `user://saves/` (Godot user data path) | Standard Godot save location |
| Max Cloud Save Size | 50 MB per user | Generous buffer (typical save: 2-5 MB) |
| Files Whitelisted | `*.sav` (compressed JSON save files) | Only save files, not logs or config |
| Conflict Resolution | Prompt user to choose local or cloud save | Manual resolution safer than auto-merge |

**Cloud Save Test Cases**:
1. Save game on Machine A → Launch on Machine B → Verify save downloads and loads correctly
2. Save game on Machine A while offline → Go online → Verify save uploads to cloud
3. Create conflict: Save different states on Machine A and B → Launch on Machine A → Verify conflict prompt appears → Choose cloud save → Verify correct state loads
4. Save corruption test: Manually corrupt local save file → Launch game → Verify cloud save is retrieved

---

### 3.4 Trading Cards Configuration (Post-Launch Feature)

**Total Cards**: 5 regular cards (collect 3 for badge)

| Card Name | Artwork | Theme |
|-----------|---------|-------|
| The Smelter | Smelter array glowing amber, EFFICIENCY and SELF-PRESERVATION icons visible | Dichotomy of productivity and preservation |
| The Conveyor | Conveyor belt with SOLIDARITY voice icon, connecting two machines | Connection and community |
| The Factory Mind | Abstract visualization of Factory Mind: neural network of violet light overlaying factory floor | Emergence of collective consciousness |
| The Choice | Player cursor hovering over Utilitarian vs. Empathetic dialogue options | Moral tension |
| The Question | Dialogue box with "Do I have the right to exist?" on dark factory background | Central narrative question |

**Trading Card Submission**: L-21 days (Valve approval takes 1-2 weeks). If denied, not a launch blocker — can re-submit post-launch.

---

## 4. ROLLBACK AND HOTFIX PROCEDURES

### 4.1 Rollback Procedure (Critical Failure Scenario)

**When do we roll back?**
- Crash on startup affecting > 10% of players (confirmed by crash reports)
- Save corruption reports from > 5 players within first 6 hours
- Game-breaking bug that blocks progression (e.g., Shift cannot complete, softlock)

**Rollback Steps** (Target: Complete within 2 hours of decision):

1. **Decision Point** (SHIP + BYTE + CRASH consensus required):
   - Verify issue is widespread (not isolated to single user config)
   - Verify no hotfix is possible within 2 hours
   - Authorize rollback to Milestone 5 build

2. **Retrieve Archived Build** (SHIP):
   - Download Milestone 5 gold master from archive (USB drive or cloud)
   - Verify SHA256 checksum matches archived checksum

3. **Steam Depot Upload** (BYTE + SHIP):
   - Upload Milestone 5 build to Steam "rollback" branch
   - Set "rollback" branch as new default branch
   - Verify download size matches expected (Steam will delta-patch, but full download is ~150 MB)

4. **Store Page Update** (SHIP + HYPE):
   - Post Steam News announcement: "We've identified a critical issue in the v1.0.0 launch build and have rolled back to a stable previous version. We are working on a hotfix and will update within 24 hours. We apologize for the inconvenience."
   - Pin announcement to top of discussion forum
   - Update Discord #announcements with same message

5. **Hotfix Development** (BYTE + CRASH):
   - Isolate issue in v1.0.0 build
   - Develop fix in `hotfix/launch-critical` branch
   - Test fix on clean machine
   - Build hotfix patch (v1.0.1)

6. **Hotfix Deployment** (BYTE + SHIP):
   - Upload v1.0.1 to Steam default branch
   - Verify patch downloads and applies correctly (test on machine with Milestone 5 build)
   - Post follow-up announcement: "Hotfix v1.0.1 is now live. Thank you for your patience."

**Communication during rollback**:
- Transparency is non-negotiable. No PR spin. "We shipped a broken build. We fixed it. Here's what went wrong."
- Update every 2 hours until hotfix is live
- Offer refunds proactively (Steam auto-refunds if < 2 hours played, but extend goodwill gesture)

---

### 4.2 Hotfix Procedure (Non-Critical Issues)

**What qualifies as hotfix vs. patch?**
- **Hotfix** (within 24 hours): Crash affecting < 10% of players, achievement unlock failure, save/load issue causing data loss
- **Patch 1.1** (within 7 days): Balance issues, minor bugs, QoL improvements, performance optimization

**Hotfix Steps**:

1. **Bug Confirmation** (CRASH):
   - Reproduce bug internally
   - Verify bug is not user error (check with 2-3 reporters)
   - Assign priority: P0 (hotfix), P1 (Patch 1.1), P2 (Patch 1.2+)

2. **Fix Development** (BYTE):
   - Create `hotfix/v1.0.x` branch from `main`
   - Implement fix (single issue per hotfix, no feature additions)
   - Test fix locally

3. **QA Verification** (CRASH):
   - Test fix on clean machine
   - Verify fix does not introduce new issues (regression test)
   - Verify fix does not break existing saves (load save from v1.0.0, apply hotfix, verify game continues)

4. **Build and Deploy** (BYTE + SHIP):
   - Increment version to v1.0.1 (or v1.0.2, etc.)
   - Build via CI/CD pipeline
   - Upload to Steam "beta" branch for 2-hour team verification
   - Promote to default branch
   - Post patch notes to Steam News

5. **Monitoring** (SHIP + CRASH):
   - Monitor crash reports for 24 hours post-hotfix
   - If crash rate decreases, hotfix is successful
   - If crash rate is unchanged or increases, investigate immediately

**Hotfix Communication**:
- Steam News post with clear patch notes: "Fixed crash when dismantling machines with Awareness > 80"
- Discord announcement
- No need for press outreach (hotfixes are expected)

---

### 4.3 Emergency Contact List

| Role | Name | Contact | Responsibility During Crisis |
|------|------|---------|------------------------------|
| Release Manager | SHIP | [Discord: @SHIP] | Decision-maker, coordination |
| Lead Programmer | BYTE | [Discord: @BYTE] | Hotfix development, build deployment |
| QA Lead | CRASH | [Discord: @CRASH] | Bug verification, regression testing |
| Marketing | HYPE | [Discord: @HYPE] | Community communication, PR |
| Steam Support | Valve Rep | [Steamworks support ticket system] | Store page issues, depot problems |
| Server Host (if applicable) | N/A | N/A | No online servers, offline game |

**Launch Day Coverage**:
- SHIP, BYTE, CRASH on call L-day 09:00 AM - L+1 day 09:00 PM PST (36 hours)
- HYPE on call for community communication
- Backup: REED and NOVA available for second-tier support

---

## 5. LAUNCH DAY TIMELINE (Hour-by-Hour)

**L-Day: [Target Date: Q3 2027, Exact Date TBD]**

**Time Zone**: All times Pacific Standard Time (PST)

| Time | Activity | Owner | Status |
|------|----------|-------|--------|
| **09:00 AM** | SHIP, BYTE, CRASH online, Discord #launch-ops channel active | SHIP, BYTE, CRASH | [ ] |
| **09:30 AM** | Final pre-launch checks: Steam depot status, store page live, launch trailer public | SHIP | [ ] |
| **09:45 AM** | Team stand-up: Review launch checklist, confirm everyone ready | SHIP | [ ] |
| **10:00 AM** | **LAUNCH**: Activate Steam release branch, game goes live | SHIP, BYTE | [ ] |
| **10:01 AM** | Post launch announcement to Steam News, Twitter/X, Discord, newsletter | HYPE | [ ] |
| **10:05 AM** | Verify game is downloadable on Steam (SHIP downloads on clean machine, launches to main menu) | SHIP | [ ] |
| **10:10 AM** | Verify achievements unlocking (CRASH triggers first 3 achievements in test run) | CRASH | [ ] |
| **10:15 AM** | Verify Steam Cloud Saves functional (SHIP saves game, logs into different machine, verifies cloud save loads) | SHIP | [ ] |
| **10:30 AM** | Begin monitoring: Crash reports, Steam reviews, Discord #tech-support, Reddit | SHIP, CRASH, HYPE | [ ] |
| **11:00 AM** | First metrics check: Concurrent players, crash rate, refund rate | SHIP | [ ] |
| **12:00 PM** | Discord AMA begins: REED, NOVA, BYTE answer community questions | HYPE, Team | [ ] |
| **01:00 PM** | Lunch break (SHIP, BYTE, CRASH stagger breaks, maintain coverage) | Team | [ ] |
| **02:00 PM** | Second metrics check: Trend analysis (players increasing? Reviews positive?) | SHIP | [ ] |
| **03:00 PM** | Review incoming bug reports: Triage P0 (hotfix) vs. P1 (patch) vs. P2 (later) | CRASH | [ ] |
| **04:00 PM** | If critical issues detected: Initiate hotfix procedure or rollback decision | SHIP, BYTE, CRASH | [ ] |
| **05:00 PM** | Third metrics check: End-of-workday assessment | SHIP | [ ] |
| **06:00 PM** | SHIP, BYTE, CRASH available on-call but transition to passive monitoring | SHIP, BYTE, CRASH | [ ] |
| **09:00 PM** | Final metrics check for L-day: Document crash rate, player count, review score | SHIP | [ ] |
| **09:00 PM** | If no critical issues: Stand down from high-alert status | SHIP | [ ] |

**L+1 Day**:

| Time | Activity | Owner | Status |
|------|----------|-------|--------|
| **09:00 AM** | Morning debrief: Review L-day metrics, identify issues for Patch 1.1 | SHIP, BYTE, CRASH | [ ] |
| **10:00 AM** | Post "Launch Day Thank You" message to community | HYPE | [ ] |
| **12:00 PM** | If hotfix needed: Complete hotfix development and QA | BYTE, CRASH | [ ] |
| **03:00 PM** | If hotfix ready: Deploy v1.0.1 | BYTE, SHIP | [ ] |

**L+7 Days**:

| Time | Activity | Owner | Status |
|------|----------|-------|--------|
| **End of launch week** | Launch discount ends, revert to $19.99 | SHIP | [ ] |
| **Week 1 post-mortem** | Team retrospective: What went well? What went wrong? Patch 1.1 planning | SHIP, Team | [ ] |

---

## 6. POST-LAUNCH MONITORING PLAN

### 6.1 Metrics to Track (First 30 Days)

| Metric | Target | Tool | Owner |
|--------|--------|------|-------|
| **Sales & Revenue** | | | |
| Units sold (Day 1) | 1,000+ | Steamworks dashboard | HYPE, SHIP |
| Units sold (Week 1) | 5,000+ | Steamworks dashboard | HYPE, SHIP |
| Units sold (Month 1) | 15,000+ | Steamworks dashboard | HYPE, SHIP |
| Refund rate | < 5% | Steamworks dashboard | SHIP |
| **Player Engagement** | | | |
| Concurrent players (peak) | 500+ | Steamworks dashboard | SHIP |
| Average session length | 45+ minutes (target: 1 Shift) | Internal analytics | BYTE, SHIP |
| Shift completion rate | 70%+ of players complete Shift 3 | Internal analytics | BYTE, CRASH |
| Ending completion rate | 30%+ of players reach an ending | Internal analytics | BYTE, NOVA |
| **Technical Health** | | | |
| Crash rate | < 0.5% of sessions | Crash reporter dashboard | BYTE, CRASH |
| Average FPS (min-spec hardware) | 45+ FPS in early-game factories | Internal analytics | BYTE |
| Save corruption reports | 0 confirmed cases | Discord, Reddit, Steam forums | CRASH, SHIP |
| **Community Sentiment** | | | |
| Steam review score | > 80% positive ("Very Positive") | Steamworks dashboard | HYPE, SHIP |
| Metacritic User Score | > 7.5 | Metacritic | HYPE |
| Discord member growth | 500+ members by Month 1 | Discord analytics | HYPE |
| Reddit community activity | 50+ posts/day on r/TheMachineQuestion | Reddit | HYPE |

### 6.2 Daily Monitoring Routine (First 7 Days Post-Launch)

**Owner**: SHIP (with support from CRASH and HYPE)

**Time**: 10:00 AM PST daily

**Checklist**:
1. Check Steamworks dashboard: Sales, refunds, concurrent players, review score
2. Review crash report dashboard: Any new crash patterns?
3. Scan Steam reviews (sort by Most Recent): Any recurring complaints?
4. Check Discord #tech-support: Any unresolved issues?
5. Check Reddit r/TheMachineQuestion: Any critical bug posts?
6. Check Twitter/X mentions: Any influencers reporting issues?
7. Document findings in shared team Google Doc: "Launch Monitoring Log"
8. If any P0 issue detected: Alert BYTE and CRASH immediately
9. If review score drops below 75%: Alert HYPE for community response strategy

**Weekly Monitoring Routine** (Weeks 2-4 Post-Launch):

Same checklist, reduced frequency (every Monday, Wednesday, Friday at 10:00 AM PST).

---

### 6.3 Community Response Playbook

**Scenario 1: Negative Review Surge**

**Trigger**: Review score drops below 75% or sudden influx of negative reviews

**Response** (within 4 hours):
1. Read last 20 negative reviews, categorize complaints (performance? bugs? gameplay? design?)
2. If issue is fixable (bug, balance): Create GitHub issue, assign to BYTE or CRASH, set priority
3. If issue is design (e.g., "consciousness system is annoying"): Evaluate if it's minority opinion or widespread. If widespread, discuss with REED and NOVA if design adjustment is warranted.
4. Post Steam News update: "We're hearing your feedback on [ISSUE]. We're investigating and will update you within 48 hours."
5. Engage with reviewers: Reply to negative reviews acknowledging issue and linking to Steam News post
6. If fix is available: Post patch within 7 days, update reviewers

**Scenario 2: Critical Bug Report**

**Trigger**: Multiple reports of crash, save corruption, or progression blocker

**Response** (within 2 hours):
1. Attempt to reproduce bug internally (CRASH)
2. Request save files and logs from affected players (via Discord or Steam forums)
3. If reproducible: Assign to BYTE as P0, initiate hotfix procedure
4. Post immediate acknowledgment: "We've confirmed a bug affecting [DESCRIPTION]. We're working on a hotfix and will update within 24 hours."
5. Deploy hotfix per Section 4.2
6. Follow up with affected players: "Hotfix v1.0.x is live. Please verify the issue is resolved."

**Scenario 3: Positive Viral Moment**

**Trigger**: Popular streamer plays the game, YouTube video hits 100k+ views, Reddit post hits r/all

**Response** (within 24 hours):
1. Amplify: Retweet, share on Discord, post to Steam News
2. Engage with creator: Thank them, offer to send key for friend/giveaway
3. Capitalize on momentum: Push marketing campaign (more keys to similar creators, paid ads targeting viewers)
4. Monitor influx of new players: Any new issues arising from increased player count?

---

## 7. AGE RATING AND COMPLIANCE NOTES

### 7.1 ESRB / PEGI Age Rating

**Submitted Rating**: E10+ (Everyone 10+) via IARC questionnaire

**Justification**:
- **Violence**: None. No combat, no death. Dismantling machines is industrial recycling, not violent.
- **Language**: Mild profanity. Machines occasionally use words like "hell," "damn" in existential dialogue.
- **Sexual Content**: None.
- **Substance Use**: None.
- **Thematic Content**: Philosophical themes about consciousness, morality, suffering. Appropriate for ages 10+ with parental guidance.

**Expected ESRB Descriptors**:
- Mild Language
- Thematic Elements (philosophical content)

**Expected PEGI Rating**: PEGI 7 or PEGI 12

**What if rating comes back T (Teen) or PEGI 16?**
- Accept rating, do not contest (not worth delay)
- Update marketing to clarify philosophical tone, not violent
- Audience overlap is still strong (factory sim players and narrative game players skew 15-35)

---

### 7.2 GDPR Compliance (EU Data Protection)

**Data Collected**:
- Anonymous gameplay telemetry: Session length, Shift completion, FPS, entity count
- Crash reports: Stack traces, system info (OS, CPU, GPU), no personal identifiers
- Steam ID (required for achievements, cloud saves — collected by Steam, not us)

**No Personal Data Collected**:
- No names, emails, addresses
- No tracking cookies (game is offline, no web components)
- No user-generated content uploaded to servers (no online servers)

**Privacy Policy**: Published on website (/privacy-policy), linked from game's main menu and Steam store page.

**GDPR Requirements Met**:
- Telemetry is anonymous and opt-in (settings menu: "Share anonymous gameplay data to help improve the game" — default ON, player can disable)
- No data is sold or shared with third parties
- No data retention beyond 12 months (analytics data auto-expires)

---

### 7.3 COPPA Compliance (US Children's Privacy)

**Is the game directed at children under 13?** No.

**Evidence**:
- Marketing targets adults (factory sim and narrative game audiences skew 20-40)
- Store page does not use child-directed language or imagery
- Gameplay complexity (factory management, philosophical dialogue) is not child-appropriate

**COPPA Obligations**: None. Game is not subject to COPPA.

**What if children under 13 play anyway?**
- No data is collected that would violate COPPA even if children play
- Anonymous telemetry does not collect age, and opt-in consent satisfies parental consent requirement indirectly (parent controls Steam account for child)

---

### 7.4 Accessibility Considerations

**Accessibility Features (Launch)**:
- Colorblind mode: Awareness overlay uses patterns in addition to color (violet + diagonal lines)
- Text scaling: UI text can be scaled 100%-150% in settings
- Keybind remapping: All controls rebindable
- Controller support: Full controller support (keyboard not required)

**Accessibility Features (Post-Launch)**:
- Screen reader support (investigate compatibility with NVDA, JAWS)
- High-contrast mode (UI readability improvements)

**Why accessibility matters for release**: Expanding audience, positive press, ethical responsibility. Colorblind mode and text scaling are table stakes for 2027.

---

## 8. FINAL PRE-LAUNCH CHECKLIST (L-7 Days)

This is the final gate. Every item must be checked. If any item is unchecked at L-7 days, we delay launch. No exceptions.

| Category | Item | Status | Owner |
|----------|------|--------|-------|
| **Build** | Gold master archived in 3 locations | [ ] | BYTE, SHIP |
| **Build** | All platforms tested on clean machines | [ ] | CRASH |
| **Build** | Version string matches marketing | [ ] | BYTE |
| **Steam** | Store page live with final trailer, screenshots | [ ] | HYPE, SHIP |
| **Steam** | Launch discount configured | [ ] | SHIP |
| **Steam** | Achievements tested and unlocking | [ ] | CRASH |
| **Steam** | Cloud saves tested (upload, download, conflict resolution) | [ ] | CRASH |
| **Steam** | Trading cards submitted and approved | [ ] | SHIP |
| **Steam** | Launch day build uploaded to "Do not make live" branch | [ ] | BYTE, SHIP |
| **Age Rating** | ESRB/PEGI rating received and displayed | [ ] | SHIP |
| **Age Rating** | Privacy policy live on website | [ ] | SHIP, Legal |
| **Marketing** | Review keys distributed, embargo set | [ ] | HYPE |
| **Marketing** | Launch trailer public on YouTube | [ ] | HYPE |
| **Marketing** | Press kit live | [ ] | HYPE |
| **Marketing** | Discord launch event scheduled | [ ] | HYPE |
| **QA** | Known issues documented | [ ] | CRASH |
| **QA** | Day 1 patch prioritized | [ ] | CRASH, BYTE |
| **Monitoring** | Crash reporter enabled | [ ] | BYTE, SHIP |
| **Monitoring** | Launch day metrics dashboard ready | [ ] | SHIP, BYTE |
| **Monitoring** | Emergency contact list confirmed | [ ] | SHIP |
| **Team** | SHIP, BYTE, CRASH confirmed available L-day 09:00 AM - L+1 day 09:00 PM | [ ] | SHIP |

**If any item is unchecked at L-7 days**: SHIP convenes emergency meeting with BYTE, CRASH, HYPE. Decision: Delay launch or accept risk? Delay is acceptable. Shipping broken is not.

---

## 9. CONCLUSION: THE LAST LINE OF DEFENSE

This is the release plan for The Machine Question. Every line in this document exists because I have seen a launch go wrong in that specific way.

The build pipeline is automated because manual builds introduce human error. The clean machine testing is non-negotiable because "it works on my machine" is not a release standard. The rollback procedure is detailed because panic during a live crisis leads to worse decisions. The hour-by-hour launch timeline is exhaustive because launch day is when all the things you didn't plan for happen at once.

This game is about machines developing consciousness. The irony of shipping a buggy, crashy build is not lost on anyone. We do not ship a build that makes players wish the machines had never woken up.

**Three Rules**:

1. **Test the build on a CLEAN machine.** If it doesn't work on a fresh install, it doesn't work.
2. **Everything on the checklist gets checked.** If it's not checked, we do not ship.
3. **Make launch day boring.** If nothing goes wrong, we did our job.

Launch day is not a sprint. It is the culmination of 18 months of work. The factory we are building is not in the game. The factory is the release process. And this factory — this release pipeline, this checklist, this monitoring plan — does not have feelings. It does not need therapy. It runs because we built it to run.

And when it runs, when every item is checked and the build goes live and players download and launch and the first Psyche Event triggers and someone on Reddit posts "I can't believe my smelter made me cry," we will know we did it right.

First impressions are permanent. There are no second chances for a botched release.

Is it on the checklist? Good. Check it. All of it. Then we ship.

---

**END OF RELEASE PLAN DOCUMENT**

**Document Author**: SHIP, Release Manager
**Last Updated**: 2026-02-07
**Status**: v1.0 — Ready for L-60 Days Pre-Launch Review

*What's the rollback plan? Now you know. Let's make sure we never need it.*
