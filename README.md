# AE Pie Slice Tool

A powerful, expression-driven Adobe After Effects ScriptUI panel for generating parametric circular sectors, pie slices, arcs, and elliptical wedges as native Shape Layers.

Designed for motion designers, infographic artists, and UI animators who need clean, animatable pie charts and circular slices with independent corner rounding and zero visual artifacts.

---

## ✨ Features

- **Native Shape Layers**: Generates clean, native vector paths with a Fill inside After Effects—no external assets, trim path hacks, or complex track mattes required.
- **Parametric & Expression-Driven**: The generated shape is powered by an optimized After Effects expression that recalculates vertices and tangents in real time.
- **Full Keyframe & Rigging Support**: All parameters are exposed as standard Effect Controls (Sliders and Checkboxes) on the layer. Keyframe them, link them to expressions, or export them to Essential Graphics / MOGRTs.
- **Circular & Elliptical Sectors**: Use uniform radius or enable **Separate X / Y Radii** for elliptical slices while preserving tangent continuity.
- **Arbitrary Angles**: Set Start Angle and End Angle in degrees, supporting sweeps up to full 360° and both clockwise and counter-clockwise directions.
- **Independent Per-Corner Rounding**:
  - **Vertex A**: Center apex of the pie.
  - **Vertex B**: Outer corner at the start angle.
  - **Vertex C**: Outer corner at the end angle.
- **Intelligent Overlap Protection**: Built-in geometric solver with strict priority (`A > C > B`) automatically clamps radii so corners never collide, invert, or glitch even when animated to extreme values.
- **Dockable ScriptUI Panel**: Run as a floating tool window or dock it seamlessly into your After Effects workspace.

---

## 📐 Corner Geometry Overview

```
                 Arc (B -> C)
              . - ~ ~ ~ - .
          B *               * C
           \                 /
            \               /
   Start Edge\             / End Edge
              \           /
               \         /
                \       /
                 \     /
                  \   /
                    *
                    A (Centre)
```

- **Corner A (Center)**: Rounded inward at the pie apex.
- **Corner B (Start Angle)**: Rounded transition between the start radial edge and the outer arc.
- **Corner C (End Angle)**: Rounded transition between the outer arc and the end radial edge.

---

## 🚀 Installation

### Option 1: Dockable Panel (Recommended)
1. Download or clone this repository.
2. Copy `Pie_Slice_Generator.jsx` into your After Effects `ScriptUI Panels` directory:
   - **Windows**:
     ```text
     C:\Program Files\Adobe\Adobe After Effects <Version>\Support Files\Scripts\ScriptUI Panels\
     ```
   - **macOS**:
     ```text
     /Applications/Adobe After Effects <Version>/Scripts/ScriptUI Panels/
     ```
3. Restart After Effects (if open).
4. Access the panel from the top menu: **Window > Pie_Slice_Generator.jsx**.

### Option 2: Run Without Installing
1. In After Effects, navigate to **File > Scripts > Run Script File...**
2. Browse to and select `Pie_Slice_Generator.jsx`.

---

## 🛠️ Usage

1. Open or select an active composition in After Effects.
2. Open the **Pie / Slice Generator** panel.
3. Configure your initial parameters:
   - **Dimensions**: Set Radius X (and optionally enable Ellipse for separate Radius Y).
   - **Angles**: Set the Start Angle and End Angle in degrees.
   - **Corner Rounding**: Enable "Round Corners" and specify individual radii for A (centre), B (start), and C (end).
4. Click **Create Pie Slice Shape Layer**.
5. Select the newly generated `Pie Slice Shape` layer and switch to the **Effect Controls** panel (`F3`) to animate or tweak any value on the fly.

---

## 🎛️ Exposed Controls Reference

Once created, the layer contains the following controls in its **Effect Controls** panel:

| Control Name | Type | Description |
|---|---|---|
| **Radius X** | Slider | Horizontal radius of the pie / arc in pixels. |
| **Radius Y** | Slider | Vertical radius in pixels (active when *Use Ellipse* is enabled). |
| **Use Ellipse** | Checkbox | Toggles between uniform circular radius and independent X/Y radii. |
| **Start Angle** | Slider | Starting angle in degrees (Corner B). |
| **End Angle** | Slider | Ending angle in degrees (Corner C). |
| **Round Corners** | Checkbox | Master toggle for corner rounding calculations. |
| **Corner Radius A** | Slider | Rounding radius at the center apex (Vertex A). |
| **Corner Radius B** | Slider | Rounding radius at the start corner (Vertex B). |
| **Corner Radius C** | Slider | Rounding radius at the end corner (Vertex C). |

---

## 💡 Tips & Use Cases

- **Pie & Donut Charts**: Create dynamic, animated infographics by stacking multiple slice layers with keyed Start/End angles.
- **Dial & Radial Gauges**: Animate slice sweeps to build dashboard speedometers, battery meters, or audio visualizer segments.
- **UI Progress Rings & Buttons**: Use rounded corner slices for modern curved mobile UI elements.
- **Overlapping Corners**: When creating sharp acute slices, the solver ensures Vertex A retains maximum rounding priority, gently adjusting B and C to prevent self-intersections.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
