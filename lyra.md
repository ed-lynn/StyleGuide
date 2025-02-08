# UE5 Style Guide

# THIS IS A DRAFT

*Heavily inspired by the [Gamemakin](https://gamemak.in) UE5 Style Guide.*

# Lyra Framework WIP

*Lyra Specific Asset Naming Convention goes here
*most links in lyra section are broken as shit. currently formatting

<a name="toc-lyra"></a>
## Lyra Table of Contents

> 1. [Asset Naming Conventions](#lyra)
> 1. [Plugin Directory Structure](#structure-plugin)
> 1. [Levels / Maps / Level Instances](#maps-lyra)
> 1. [Textures](#textures)

#### Sections

> 1.1 [Lyra Primary Assets](#lyra-prime)

> 1.7 [Miscellaneous](#lyra-misc)

> 1.11 [Common UI User Interface](#lyra-ui)


<a name="lyra-prime"></a>
<a name="1.1"></a>
#### 1.2.1 Lyra Primary Data Assets

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Experience Definition   | BP_        | _EX        | [System/Experiences](#2.4)       |
| User-Facing Experience  | DA_        | _UX        | [System/Experiences](#2.4)       |
| Experience Action Set   | DA_        | _AS        |                                  |
| Pawn Data               | DA_        | _PD        | [System/Playlists](#2.4)         |
| Input Config            | DA_        | _IG        | [Input](#2.4)                    |
| Texture                 | T_         | _?         | See [Textures](#anc-textures)    |

<a name="lyra-misc"></a>
<a name="1.2.7"></a>
### 1.2.7 Miscellaneous

| Asset Type                 | Prefix     | Suffix     | Notes                            |
| -------------------------- | ---------- | ---------- | -------------------------------- |
| Animated Vector Field      | VFA_       |            |                                  |
| Camera Anim                | CA_        |            |                                  |
| Color Curve                | Curve_     | _Color     |                                  |
| Curve Table                | Curve_     | _Table     |                                  |
| Data Asset                 | *_         |            | Prefix should be based on class. |
| Data Table                 | DT_        |            |                                  |
| Float Curve                | Curve_     | _Float     |                                  |
| Foliage Type               | FT_        |            |                                  |
| Force Feedback Effect      | FFE_       |            |                                  |
| Landscape Grass Type       | LG_        |            |                                  |
| Landscape Layer            | LL_        |            |                                  |
| Matinee Data               | Matinee_   |            |                                  |
| Media Player               | MP_        |            |                                  |
| Object Library             | OL_        |            |                                  |
| Redirector                 |            |            | These should be fixed up ASAP.   |
| Sprite Sheet               | SS_        |            |                                  |
| Static Vector Field        | VF_        |            |                                  |
| Substance Graph Instance   | SGI_       |            |                                  |
| Substance Instance Factory | SIF_       |            |                                  |
| Touch Interface Setup      | TI_        |            |                                  |
| Vector Curve               | Curve_     | _Vector    |                                  |

<a name="lyra-ui"></a>
<a name="1.2.11"></a>
### 1.2.11 User Interface

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Font                    | Font_      |            |                                  |
| Slate Brush             | Brush_     |            |                                  |
| Slate Widget Style      | Style_     |            |                                  |
| Widget Blueprint        | WBP_       |            |                                  |

**[⬆ Back to Top](#table-of-contents)**


<a name="2"></a>
<a name="structure"></a>
## 2. Content Directory Structure

Equally important as asset names, the directory structure style of a project should be considered law. Asset naming conventions and content directory structure go hand in hand, and a violation of either causes unneeded chaos.

There are multiple ways to lay out the content of a ue5 project. In this style, we will be using a structure that relies more on filtering and search abilities of the Content Browser for those working with assets to find assets of a specific type instead of another common structure that groups asset types with folders.

> If you are using the prefix [naming convention](#1.2) above, using folders to contain assets of similar types such as `Meshes`, `Textures`, and `Materials` is a redundant practice as asset types are already both sorted by prefix as well as able to be filtered in the content browser.

<a name="2e1"><a>
### 2e1 Example Lyra uBer Feature Plugin [UFP]
<pre>
|-- Content
|-- Plugins
|   |-- <a href="#2.2">uFrame Source Content</a>
    |-- <a href="#2.2">ShooterCore</a>
        |-- Characters
        |   |-- Cameras
        |   |-- Cosmetics
        |   |-- Heroes
        |   |   |-- Pipes
        |   |-- Nature
        |   |   |-- Ambient
        |   |   |-- Foliage
        |   |   |-- Rocks
        |   |   |-- Trees
        |   |-- Office
        |-- Environment
        |   |--Props
        |-- Experiences
        |   |-- Bob
        |   |-- Common
        |   |   |-- <a href="#2.7">Animations</a>
        |   |   |-- Audio
        |   |-- Jack
        |   |-- Steve
        |   |-- <a href="#2.1.3">Zoe</a>
        |-- <a href="#2.5">Core</a>
        |   |-- Characters
        |   |-- Engine
        |   |-- <a href="#2.1.2">GameModes</a>
        |   |-- Interactables
        |   |-- Pickups
        |   |-- Weapons
        |-- GUI
        |   |   |-- Widgets
        |   |   |-- Cursors
        |   |   |   |-- Cursor.png
        |   |-- Fire
        |   |-- Weather
        |-- <a href="#2.4">Maps</a>
        |   |-- MainMenu
        |   |-- DevMap
        |   |-- MainGameMap
        |   |-- <a href="#2.7">LevelInstances</a>
        |   |   |-- Town
        |   |   |-- Bank
        |   |   |-- Random POI
        |-- Input
        |   |-- IMC_Default
        |   |-- Actions
        |   |   |-- IA_Move
        |   |   |-- IA_Look
        |-- System
        |   |-- Experiences
        |   |-- Playlists
        |   |   |-- DesertEagle
        |   |   |-- RocketPistol
</pre>

The reasons for this structure are listed in the following sub-sections.

### Sections

> 2.1 [Folder Names](#structure-folder-names)

> 2.2 [Top-Level Folders](#structure-top-level)

> 2.3 [Developer Folders](#structure-developers)

> 2.4 [Maps](#structure-maps)

> 2.5 [Core](#structure-core)

> 2.6 [`Assets` and `AssetTypes`](#structure-assettypes)

> 2.7 [Large Sets](#structure-large-sets)

<a name="2.4"></a>
<a name="structure-maps"></a>
### 2.4 All Map[<sup>*</sup>](#terms-level-map) Files Belong In A Folder Called Maps

because Asset Manager