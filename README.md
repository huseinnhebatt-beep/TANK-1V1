# TANK-1V1# GDD — **TANK 1V1: NUCLEAR FRONT**

**Genre:** 2D Pixel Art • Tank Combat • 1v1 PvP
**Platform:** PC / Web / Mobile
**Camera:** Side View / 2D
**Mode utama:** Player vs Player 1v1
**Match Duration:** ±3–7 menit
**Visual:** Pixel Art militer, post-apocalyptic, industrial
**Core Loop:** Bergerak → membidik → menembak → menghancurkan lawan → menguasai arena

---

## 1. HIGH CONCEPT

**TANK 1V1: NUCLEAR FRONT** adalah game pertarungan tank 2D dari samping di mana dua pemain bertempur dalam arena kecil menggunakan tank dengan kemampuan berbeda.

Pemain harus memanfaatkan:

* Terrain
* Platform
* Bangunan
* Cover
* Elevasi
* Senjata utama
* Missile
* Secondary turret
* Power-up
* Nuclear Strike

Tujuan utama:

> **Hancurkan tank lawan sebelum tank milikmu dihancurkan.**

---

# 2. REFERENSI VISUAL GAME

Game menggunakan empat kelompok asset utama yang sudah kamu buat:

### A. Map / Environment

Atlas map berisi:

* Ground
* Platform
* Water
* Lava
* Background
* Building
* Ruins
* Debris
* Trees
* Fence
* Ladder
* Signs
* Props
* Smoke
* Fire
* Particles
* Military vehicles

### B. Player Tank

Spritesheet tank player menyediakan:

* Idle
* Move Right
* Move Left
* Turn Right
* Turn Left
* Shoot Right
* Shoot Left
* Hit
* Explode
* Variant tank

### C. Boss Tank

Boss spritesheet menyediakan:

* Idle
* Movement
* Main Cannon Attack
* Missile Launch
* Secondary Turret Attack
* Take Damage
* Destroyed
* Projectile
* Smoke / Debris

### D. Nuclear Explosion

Nuclear spritesheet:

**32 frame**

untuk animasi:

> Flash → Fireball → Mushroom Cloud → Smoke → Dissipation

---

# 3. CORE GAMEPLAY

## Match Flow

```text
MAIN MENU
    ↓
SELECT TANK
    ↓
SELECT MAP
    ↓
MATCH 1V1
    ↓
FIGHT
    ↓
TANK DESTROYED
    ↓
VICTORY / DEFEAT
    ↓
REPLAY / MENU
```

---

# 4. GAME ARENA

Arena menggunakan format side-view.

Contoh layout:

```text
             ┌───────────────┐
             │   PLATFORM    │
       P1    └───────┬───────┘
                      │
──────────────────────┴──────────────
       BUILDING             P2
───────────────┐      ┌──────────────
               │      │
               │      │
═══════════════╧══════╧═══════════════
             GROUND
```

Arena harus memiliki:

* Spawn Player 1
* Spawn Player 2
* Ground
* Elevated platform
* Cover
* Destructible objects
* Environmental hazards

---

# 5. TERRAIN

## Ground

Terrain utama untuk pergerakan tank.

Karakteristik:

* Bisa dilewati tank
* Bisa menjadi cover
* Memiliki variasi tile
* Bisa dibuat destructible pada beberapa map

---

## Platform

Platform digunakan untuk:

* Elevasi
* Sniping
* Tactical positioning
* Menghindari projectile

---

## Water

Water berfungsi sebagai hazard.

Contoh:

**Tank biasa**

```text
MASUK AIR
↓
Movement Speed -50%
↓
Turret tetap dapat menembak
```

Tank tertentu dapat memiliki resistensi terhadap water.

---

## Lava

Lava adalah environmental hazard.

Jika tank menyentuh lava:

```text
DAMAGE
+
BURN EFFECT
+
SMOKE
```

Lava dapat memberikan damage berkala.

---

# 6. DESTRUCTIBLE ENVIRONMENT

Beberapa objek dapat dihancurkan:

* Barrel
* Crate
* Fence
* Building
* Ruins
* Debris
* Tower

Contoh:

```text
TANK
 ↓
SHOOT
 ↓
BUILDING
 ↓
DAMAGE
 ↓
CRACK
 ↓
COLLAPSE
 ↓
DEBRIS
```

Hal ini membuat arena berubah selama pertandingan.

---

# 7. PLAYER TANK

Tank standar menjadi unit utama player.

### Base Stats

| Stat             |              Nilai |
| ---------------- | -----------------: |
| HP               |               1000 |
| Armor            |                100 |
| Main Damage      |                150 |
| Fire Rate        | 1 shot / 1.5 detik |
| Move Speed       |                120 |
| Rotation         |            90°/sec |
| Projectile Speed |                500 |
| Missile          |                  2 |
| Secondary Turret |              Aktif |

Nilai ini adalah **starting balance** dan dapat diubah saat prototyping.

---

# 8. TANK CONTROL

## Keyboard

| Tombol | Fungsi           |
| ------ | ---------------- |
| A      | Bergerak kiri    |
| D      | Bergerak kanan   |
| W      | Aim naik         |
| S      | Aim turun        |
| Space  | Main Cannon      |
| Q      | Missile          |
| E      | Secondary Weapon |
| Shift  | Boost            |
| R      | Reload / Ability |
| Esc    | Pause            |

Untuk PvP lokal:

### Player 1

```text
W A S D
Space
Q
E
```

### Player 2

```text
Arrow Keys
Enter
NumPad 0
NumPad 1
```

---

# 9. AIM SYSTEM

Tank dapat mengatur sudut cannon.

Contoh:

```text
          70°
           /
          /
    45° /
        /
TANK ───────────── 0°
```

Aim angle:

**-10° sampai +80°**

Tujuannya supaya pemain dapat menembak:

* Langsung
* Ke atas
* Melewati obstacle
* Dari platform

---

# 10. MAIN CANNON

Senjata utama tank.

### Gameplay

```text
PRESS SPACE
     ↓
CANNON RECOIL
     ↓
MUZZLE FLASH
     ↓
PROJECTILE
     ↓
IMPACT
     ↓
DAMAGE
```

Projectile menggunakan asset dari boss spritesheet.

Efek:

* Muzzle flash
* Projectile trail
* Impact explosion
* Smoke
* Screen shake

---

# 11. MISSILE SYSTEM

Missile digunakan sebagai senjata burst damage.

### Contoh

**Damage:** 250

**Cooldown:** 8 detik

Missile dapat:

* Mengikuti target secara ringan
* Meledak ketika terkena tank
* Meledak ketika mengenai terrain

Animasi:

```text
MISSILE READY
      ↓
LAUNCH
      ↓
TRAIL
      ↓
FLIGHT
      ↓
IMPACT
      ↓
EXPLOSION
```

---

# 12. SECONDARY TURRET

Secondary turret merupakan senjata otomatis.

Contoh:

```text
TARGET TERDEKAT
       ↓
LOCK
       ↓
AUTO FIRE
       ↓
SMALL PROJECTILES
```

Damage lebih kecil daripada main cannon tetapi fire rate lebih tinggi.

Contoh:

**Damage:** 30

**Fire Rate:** 0.25 detik

---

# 13. DAMAGE SYSTEM

Setiap tank mempunyai:

```text
HP
ARMOR
```

Contoh:

```text
Projectile Damage = 150

Armor = 50

Effective Damage
= 150 - 50
= 100
```

Armor dapat dikembangkan menjadi:

* Front Armor
* Side Armor
* Rear Armor

Sehingga positioning menjadi bagian penting dari gameplay.

---

# 14. CRITICAL HIT

Tembakan tertentu dapat mengenai critical area.

Contoh:

```text
      ┌───────┐
      │ TURRET│ ← Critical
      └───────┘
   █████████████
   █ TRACKS ████
```

Critical hit:

**+50% damage**

Efek:

* Flash
* Sparks
* Screen shake
* Critical indicator

---

# 15. TANK MOVEMENT

Tank menggunakan sistem movement berbasis track.

Animasi spritesheet:

```text
IDLE
 ↓
MOVE RIGHT
 ↓
MOVE LEFT
 ↓
TURN
```

Track animation harus berjalan ketika tank bergerak.

Ketika berhenti:

> Track berhenti.

---

# 16. TANK DAMAGE STATE

Spritesheet menyediakan animasi:

### HIT

Tank terkena serangan.

Efek:

* Flash
* Sparks
* Smoke

### CRITICAL

HP rendah.

Tank mulai:

* Mengeluarkan smoke
* Mengeluarkan sparks
* Alarm

---

# 17. DESTROYED

Jika:

```text
HP <= 0
```

maka:

```text
TANK
 ↓
EXPLOSION
 ↓
FIRE
 ↓
SMOKE
 ↓
WRECK
```

Menggunakan animation dari spritesheet tank.

---

# 18. BOSS TANK

Boss tank digunakan sebagai:

### Mode PvE tambahan

dan juga dapat digunakan sebagai:

### Tank berat / Special Tank dalam PvP.

Boss memiliki:

* Main Cannon
* Missile
* Secondary Turret
* Heavy Armor

---

# 19. BOSS ATTACK

Boss memiliki tiga serangan utama.

### MAIN CANNON

Damage besar.

### MISSILE

Projectile dengan tracking.

### SECONDARY TURRET

Rapid fire.

AI boss:

```text
SEARCH PLAYER
      ↓
CALCULATE DISTANCE
      ↓
SELECT WEAPON
      ↓
AIM
      ↓
ATTACK
      ↓
REPOSITION
```

---

# 20. NUKE / NUCLEAR STRIKE

Nuclear explosion menjadi **Ultimate Weapon**.

Asset menyediakan 32 frame.

Tahapan:

```text
FRAME 1–4
FLASH
     ↓
FRAME 5–8
FIREBALL
     ↓
FRAME 9–16
MUSHROOM CLOUD
     ↓
FRAME 17–24
SMOKE
     ↓
FRAME 25–32
DISSIPATE
```

---

# 21. NUCLEAR MECHANIC

Nuke tidak boleh langsung tersedia.

Player harus mengisi:

### NUCLEAR METER

Contoh:

```text
N U C L E A R

████████░░ 80%
```

Meter meningkat ketika:

* Memberikan damage
* Membunuh enemy
* Menghancurkan building
* Bertahan hidup

Ketika 100%:

> **NUCLEAR STRIKE READY**

---

# 22. NUCLEAR STRIKE GAMEPLAY

Player memilih lokasi target.

```text
          TARGET
            ↓
            ☢
            │
────────────────────
       ARENA
```

Kemudian:

```text
WARNING
   ↓
FLASH
   ↓
FIREBALL
   ↓
MUSHROOM CLOUD
   ↓
SHOCKWAVE
   ↓
SMOKE
```

Nuke memberikan:

* Damage sangat besar
* Knockback
* Terrain destruction
* Screen shake
* Flash effect

Untuk PvP kompetitif, damage nuke sebaiknya **besar tetapi tidak otomatis membunuh**, misalnya 60–75% HP maksimum.

---

# 23. MAP TYPES

Berdasarkan map spritesheet, game dapat memiliki beberapa arena.

## MAP 01 — GREEN VALLEY

Tema:

🌳 Grassland

Fitur:

* Tanah
* Pohon
* Platform
* Bangunan kecil

---

## MAP 02 — DESERT WARZONE

Tema:

🏜️ Desert

Fitur:

* Sand
* Ruins
* Military structures
* Debris

---

## MAP 03 — URBAN RUINS

Tema:

🏙️ Destroyed City

Fitur:

* Gedung
* Jalan
* Ruins
* Cover

---

## MAP 04 — FROZEN FRONT

Tema:

❄️ Snow

Fitur:

* Snow
* Mountain
* Ice platform
* Low visibility

---

## MAP 05 — VOLCANIC ZONE

Tema:

🌋 Lava

Fitur:

* Lava
* Rocks
* Volcano terrain
* Fire particles

---

# 24. GAME MODES

## MODE 1 — 1V1 LOCAL

Dua pemain dalam satu komputer.

```text
PLAYER 1
VS
PLAYER 2
```

---

## MODE 2 — AI BATTLE

Player melawan AI.

Difficulty:

* Easy
* Normal
* Hard
* Boss

---

## MODE 3 — BOSS BATTLE

Player:

**VS**

Boss Tank.

---

## MODE 4 — SURVIVAL

Player harus bertahan melawan beberapa tank.

---

# 25. POWER-UP

Power-up dapat muncul secara acak.

### 🔴 Repair

+25% HP

### 🟡 Armor

Damage received -30%

### 🔵 Rapid Fire

Fire rate ×2

### 🟢 Damage Boost

Damage ×1.5

### 🟣 Missile Pack

+2 Missile

### ☢ Nuclear Charge

+25% Nuclear Meter

---

# 26. UI / HUD

Layout:

```text
┌────────────────────────────────────────────┐
│ P1 HP ██████████      ☢ 70%     P2 HP ████│
│                                            │
│                                            │
│                  ARENA                     │
│                                            │
│                                            │
│                                            │
├────────────────────────────────────────────┤
│ AMMO       MISSILE       SECONDARY         │
│  ● ● ●       2             READY           │
└────────────────────────────────────────────┘
```

HUD:

* HP bar
* Armor
* Ammo
* Missile count
* Cooldown
* Nuclear meter
* Crosshair
* Timer

---

# 27. CROSSHAIR

Crosshair menunjukkan arah projectile.

```text
          +
        +   +
          +
```

Warna/status:

**Normal**

`READY`

**Cooldown**

`RELOADING`

**Nuclear**

`☢ READY`

---

# 28. CAMERA

Camera menggunakan side-view 2D.

Mode:

### Static Arena

Kamera tidak bergerak.

Cocok untuk:

> 1V1 competitive.

### Dynamic Camera

Kamera mengikuti posisi dua tank.

Cocok untuk arena besar.

---

# 29. PHYSICS

Tank:

* Gravity
* Ground collision
* Platform collision
* Projectile collision
* Explosion force
* Knockback

Projectile:

```text
Velocity
Gravity
Collision
Explosion
```

Untuk cannon, projectile dapat menggunakan trajectory.

---

# 30. DESTRUCTIBLE OBJECT

Setiap objek memiliki HP.

Contoh:

| Object         |   HP |
| -------------- | ---: |
| Crate          |   50 |
| Barrel         |   75 |
| Fence          |  100 |
| Small Building |  400 |
| Tower          |  700 |
| Heavy Building | 1000 |

---

# 31. PARTICLE EFFECT

Gunakan particle dari asset:

### Gun

* Muzzle flash
* Sparks
* Smoke

### Explosion

* Fire
* Debris
* Smoke

### Tank destroyed

* Large explosion
* Smoke
* Burning debris

### Environment

* Dust
* Fire
* Water splash
* Lava sparks

---

# 32. SOUND DESIGN

## Weapon

**Main Cannon**

> BOOM!

**Missile**

> WHOOSH!

**Secondary**

> RATATAT!

## Impact

* Metal hit
* Explosion
* Armor hit

## Tank

* Engine idle
* Engine acceleration
* Track movement
* Turret rotation

## Nuclear

Sequence:

```text
LOW RUMBLE
 ↓
WARNING SIREN
 ↓
FLASH
 ↓
BOOM
 ↓
DEEP RUMBLE
 ↓
WIND
```

---

# 33. GAME BALANCE

Target pertandingan:

**3–7 menit**

Jangan membuat tank terlalu cepat mati.

Ideal:

```text
1 hit     = 10–20% HP
critical  = 20–30%
missile   = 20–30%
nuke      = 60–75%
```

Dengan demikian pemain masih mempunyai kesempatan melakukan comeback.

---

# 34. TANK VARIANTS

Dari spritesheet tersedia:

### DEFAULT

Balanced.

### DESERT

Movement sedikit lebih cepat.

### WINTER

Armor lebih tinggi.

### JUNGLE

Camouflage / detection advantage.

### URBAN

Reload lebih cepat.

### STORM

Damage lebih tinggi.

### HEAVY

HP dan armor tinggi tetapi lambat.

Contoh balancing:

| Tank    |   HP | Damage | Speed | Armor |
| ------- | ---: | -----: | ----: | ----: |
| Default | 1000 |    150 |   100 |   100 |
| Desert  |  900 |    140 |   125 |    80 |
| Winter  | 1100 |    145 |    90 |   130 |
| Jungle  |  950 |    150 |   110 |    90 |
| Urban   |  950 |    155 |   100 |   100 |
| Storm   |  900 |    180 |    95 |    80 |
| Heavy   | 1400 |    170 |    65 |   160 |

---

# 35. WIN CONDITION

### Player menang jika:

```text
ENEMY HP = 0
```

atau

```text
ENEMY TANK DESTROYED
```

Screen:

```text
╔══════════════════════╗
║      VICTORY!        ║
║                      ║
║    PLAYER 1 WINS     ║
║                      ║
║   [REMATCH] [MENU]   ║
╚══════════════════════╝
```

---

# 36. DRAW CONDITION

Jika kedua tank hancur bersamaan:

> **DRAW**

Pemain dapat melakukan:

* Rematch
* Return Menu

---

# 37. MATCH SETTINGS

Sebelum pertandingan:

```text
MAP
[ GREEN VALLEY ]

TANK
[ DEFAULT ]

GAME MODE
[ 1V1 ]

MATCH TIME
[ 5 MIN ]

POWER UPS
[ ON ]

NUCLEAR
[ ON ]

[ START BATTLE ]
```

---

# 38. ART DIRECTION

Gaya visual harus konsisten dengan spritesheet yang diberikan:

### Style

**2D Pixel Art Military**

Karakteristik:

* Dark military palette
* Orange/red weapon effects
* Detailed tank
* Pixelated edges
* High contrast
* Industrial ruins
* Post-apocalyptic environment

### Visual hierarchy

Tank:

**PALING MENONJOL**

Environment:

**MEDIUM**

Background:

**LOW CONTRAST**

Projectile:

**HIGH CONTRAST**

---

# 39. SPRITESHEET STRUCTURE

Struktur asset yang disarankan:

```text
Assets/
│
├── Tanks/
│   ├── Player/
│   │   ├── idle.png
│   │   ├── move.png
│   │   ├── shoot.png
│   │   ├── hit.png
│   │   └── destroy.png
│   │
│   └── Boss/
│       ├── idle.png
│       ├── move.png
│       ├── cannon.png
│       ├── missile.png
│       ├── secondary.png
│       ├── damage.png
│       └── destroy.png
│
├── Environment/
│   ├── terrain.png
│   ├── platform.png
│   ├── water.png
│   ├── lava.png
│   ├── buildings.png
│   ├── ruins.png
│   └── props.png
│
├── Effects/
│   ├── explosion.png
│   ├── nuclear.png
│   ├── smoke.png
│   ├── fire.png
│   └── particles.png
│
└── UI/
    ├── hud.png
    ├── icons.png
    └── buttons.png
```

---

# 40. DEVELOPMENT PRIORITY

## PHASE 1 — PROTOTYPE

Buat terlebih dahulu:

```text
Tank
 ↓
Movement
 ↓
Aim
 ↓
Shoot
 ↓
Damage
 ↓
Destroy
```

Target:

> **Tank 1 vs Tank 2 sudah bisa bertarung.**

---

## PHASE 2 — MAP

Tambahkan:

* Ground
* Platform
* Buildings
* Props
* Background

---

## PHASE 3 — COMBAT

Tambahkan:

* Main cannon
* Missile
* Secondary turret
* Explosion
* Hit effect
* Smoke

---

## PHASE 4 — NUCLEAR

Tambahkan:

* Nuclear meter
* Target system
* 32-frame nuclear animation
* Screen shake
* Shockwave
* Terrain damage

---

## PHASE 5 — GAME SYSTEM

Tambahkan:

* Main menu
* Tank selection
* Map selection
* Pause
* Victory
* Defeat
* Rematch

---

# 41. MVP

Versi pertama **jangan langsung membuat semua fitur**.

MVP cukup:

### 1 Arena

### 2 Tank

### Movement

### Aim

### Main Cannon

### HP

### Explosion

### Win/Lose

Flow:

```text
             TANK 1
                │
                ▼
           ┌─────────┐
           │  BATTLE │
           └────┬────┘
                │
         ┌──────┴──────┐
         ▼             ▼
      TANK 1          TANK 2
      DESTROYED       DESTROYED
         │             │
         ▼             ▼
      DEFEAT         VICTORY
```

Setelah MVP stabil, baru tambahkan **missile → secondary turret → power-up → boss → nuclear strike → multiple maps**.

---

# 42. IDENTITAS GAME

### Judul

# **TANK 1V1: NUCLEAR FRONT**

### Tagline

> **AIM. FIRE. SURVIVE.**

### Core Fantasy

> **Dua tank masuk ke medan perang. Hanya satu yang keluar.**

### Pilar Gameplay

**1. AIM**
Kemampuan menentukan sudut dan timing.

**2. POSITION**
Memanfaatkan terrain dan cover.

**3. FIRE**
Memilih senjata yang tepat.

**4. SURVIVE**
Mengelola HP, armor, cooldown dan nuclear meter.

**5. DESTROY**
Hancurkan tank lawan.

---

## 43. TARGET HASIL AKHIR

Versi final idealnya terasa seperti:

```text
┌──────────────────────────────────────────────┐
│ P1 ███████████        ☢ 100%       █████ P2 │
│                                              │
│              ☢ NUCLEAR READY                │
│                                              │
│       🏢                    🏢               │
│             🚜          🚜                   │
│  ████████████████████████████████████████   │
│                                              │
│    PLAYER 1                    PLAYER 2     │
│      TANK                         TANK       │
│       ═══►         💥          ◄═══          │
└──────────────────────────────────────────────┘
```

**Inti game:** pertandingan cepat, mudah dimainkan, tetapi memiliki kedalaman dari **aiming, positioning, cooldown, terrain, dan penggunaan Nuclear Strike**.

**Langkah berikutnya yang paling berguna:** kita bisa langsung mengubah GDD ini menjadi **Game Design Document teknis untuk Unity/Godot**, lengkap dengan struktur scene, sistem Player 1 & Player 2, script tank, projectile, HP, collision, nuclear system, dan pembagian spritesheet per frame.
