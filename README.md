# HeartsOfIronMC
Hearts of Iron IV als Minecraft-Minestom-Server in Java, mit OOP, Event-System, Services, UI, Tick-Handling, KI und Game Logic.

## File Tree
```
src/
└── main/
    └── java/
        └── dev/
            └── max/
                └── hoimc/
                    ├── HOIMain.java                <-- Einstiegspunkt
                    │
                    ├── bootstrap/                 <-- Server-Start, Setup, Registrierungen
                    │   ├── Bootstrap.java
                    │   ├── PluginLoader.java
                    │   └── WorldLoader.java
                    │
                    ├── service/                   <-- Services für zentrale Systeme
                    │   ├── Service.java
                    │   ├── AbstractService.java
                    │   ├── ServiceRegistry.java
                    │   └── ServiceInitException.java
                    │
                    ├── tick/                      <-- Ticker & Zeit-Logik
                    │   ├── Tickable.java
                    │   ├── GameTicker.java
                    │   ├── DailyTick.java
                    │   ├── WeeklyTick.java
                    │   └── TickScheduler.java
                    │
                    ├── core/                      <-- Kernlogik
                    │   ├── GameManager.java
                    │   ├── GamePhase.java
                    │   └── GameState.java
                    │
                    ├── world/                     <-- Provinzen, Weltkarte etc.
                    │   ├── Province.java
                    │   ├── ProvinceType.java
                    │   ├── TerrainType.java
                    │   ├── WorldMap.java
                    │   ├── ProvinceManager.java
                    │   └── BorderCalculator.java
                    │
                    ├── player/                    <-- Spieler & Nation-Zuweisung
                    │   ├── HOIPlayer.java
                    │   ├── PlayerStats.java
                    │   ├── PlayerManager.java
                    │   ├── PlayerPermissions.java
                    │   └── PlayerNationLink.java
                    │
                    ├── nation/                    <-- Länderverwaltung
                    │   ├── Nation.java
                    │   ├── NationManager.java
                    │   ├── NationFactory.java
                    │   ├── GovernmentType.java
                    │   ├── Ideology.java
                    │   ├── FlagRenderer.java
                    │   └── DiplomacyStatus.java
                    │
                    ├── economy/                   <-- Wirtschaftssystem
                    │   ├── EconomyManager.java
                    │   ├── ResourceManager.java
                    │   ├── Factory.java
                    │   ├── CivilianFactory.java
                    │   ├── MilitaryFactory.java
                    │   ├── ConstructionProject.java
                    │   └── TradeAgreement.java
                    │
                    ├── warfare/                   <-- Kriegsführung
                    │   ├── WarManager.java
                    │   ├── War.java
                    │   ├── WarGoal.java
                    │   ├── Battle.java
                    │   ├── Army.java
                    │   ├── Division.java
                    │   ├── Equipment.java
                    │   └── FrontLine.java
                    │
                    ├── tech/                      <-- Forschung & Technologien
                    │   ├── ResearchManager.java
                    │   ├── ResearchTree.java
                    │   ├── TechNode.java
                    │   ├── TechCategory.java
                    │   ├── TechBonus.java
                    │   └── ResearchSlot.java
                    │
                    ├── events/                    <-- Spielinterne Events
                    │   ├── HOIEvent.java
                    │   ├── EventType.java
                    │   ├── EventManager.java
                    │   ├── FocusEvent.java
                    │   └── EventExecutor.java
                    │
                    ├── focus/                     <-- National Focus Trees
                    │   ├── FocusTree.java
                    │   ├── FocusNode.java
                    │   ├── FocusManager.java
                    │   └── FocusEffect.java
                    │
                    ├── ai/                        <-- KI-Verhalten
                    │   ├── AIManager.java
                    │   ├── AINationController.java
                    │   ├── DecisionMaker.java
                    │   └── StrategyModule.java
                    │
                    ├── ui/                        <-- GUIs & Interaktionen
                    │   ├── GUI.java
                    │   ├── GUIManager.java
                    │   ├── NationSelectGUI.java
                    │   ├── ProductionGUI.java
                    │   ├── ResearchGUI.java
                    │   ├── WarPanelGUI.java
                    │   └── TextFactory.java
                    │
                    ├── data/                      <-- Lade-/Speichersysteme
                    │   ├── JSONLoader.java
                    │   ├── SaveManager.java
                    │   ├── DataConstants.java
                    │   └── InitialDataLoader.java
                    │
                    ├── util/                      <-- Helferklassen
                    │   ├── ColorUtils.java
                    │   ├── MathUtils.java
                    │   ├── Logger.java
                    │   ├── LocationUtils.java
                    │   └── Timer.java
                    │
                    └── config/                    <-- Konfigurationen
                        ├── Config.java
                        ├── ServerSettings.java
                        └── GameRules.java
resources/
├── config/
│   ├── server_settings.json
│   ├── game_rules.json
│   └── logging.json
│
├── provinces/
│   ├── germany/
│   │   ├── 001_berlin.json
│   │   ├── 002_bavaria.json
│   │   ├── 003_saxony.json
│   │   └── ...
│   ├── france/
│   │   ├── 001_paris.json
│   │   ├── 002_normandy.json
│   │   ├── 003_lyon.json
│   │   └── ...
│   ├── soviet_union/
│   │   ├── 001_moscow.json
│   │   ├── 002_leningrad.json
│   │   └── ...
│   ├── united_kingdom/
│   │   ├── 001_london.json
│   │   ├── 002_manchester.json
│   │   └── ...
│   ├── usa/
│   │   ├── 001_washington.json
│   │   ├── 002_new_york.json
│   │   └── ...
│   ├── italy/
│   │   ├── 001_rome.json
│   │   ├── 002_milan.json
│   │   └── ...
│   ├── japan/
│   │   ├── 001_tokyo.json
│   │   ├── 002_osaka.json
│   │   └── ...
│   └── poland/
│       ├── 001_warsaw.json
│       ├── 002_krakow.json
│       └── ...
│
├── factories/
│   ├── military.json
│   ├── civilian.json
│   └── dockyard.json
│
├── focus_trees/
│   ├── germany_focus.json
│   ├── france_focus.json
│   └── japan_focus.json
│
├── tech/
│   ├── industry.json
│   ├── electronics.json
│   ├── infantry.json
│   ├── armor.json
│   ├── air.json
│   └── naval.json
│
├── events/
│   ├── event_anschluss.json
│   ├── event_munich_agreement.json
│   └── event_spanish_civil_war.json
│
├── ui/
│   ├── main_menu.json
│   └── tooltip_templates.json
│
└── localization/
    ├── en_us.json
    └── de_de.json

```
