# QuirkFX
QuirkFX allows you develop with JavaFX as quirk as no one has made before.

An image is better than a thousand words, here are some usage examples:

```java
// create a preset with two properties for using later
QuirkFX preset1 = QuirkFX.newPreset().setAlign("BASELINE_LEFT").setText("default text");
// alternative with same result
preset1 = QuirkFX.newPreset().setAlign(Pos.BASELINE_LEFT).setText("default text");

// create a preset with one property and including other preset for using later
QuirkFX preset2 = QuirkFX.newPreset().setTextAlign("JUSTIFY").setPreset(preset1);
// alternative with same result
preset2 = QuirkFX.newPreset().setTextAlign(TextAlignment.JUSTIFY).setPreset(preset1);

// create a label and set properties in one line
QuirkFX lblgrp = QuirkFX.newLabel().setPreset(preset1).setText("graphic label text");

// change lblgrp text alignment to CENTER
lblgrp.setTextAlign(TextAlignment.CENTER);

// create another label, set properties and use the before created label as graphic
QuirkFX lbl = QuirkFX.newLabel().setPreset(preset2).setText("label text")
		.setGraphic(lblgrp).setTextAlign("JUSTIFY");

// obtain the "warped" original javafx reference
Label lblfx = lbl.get(Label.class);

// create a button with the previous labels as graphics and return directly the warped javafx object
Button btnfx = QuirkFX.newButton().setGraphic(lblfx).get(Button.class);

// get back the graphic property value from lbl
Label lblgrpfx = lbl.get(QuirkFX.Type.GRAPHIC, Label.class);

// get back the lbl text property
String lbltext = lbl.get(QuirkFX.Type.TEXT, String.class);

// get the before javafx button and set a backgroundcolor style and text
QuirkFX.warp(btnfx).setStyle("-fx-background-color:red;").setText("this is a button");
```
QuirkFX warps (not wraps) JavaFX.

Plans are finishing support for all or at least more used properties using PipeCC precompiler and, also including a simplified superpowerful Q-notation for constructors:

```java
Q preset1 = Q.preset().setAlign(Q.BASELINE_LEFT).setText("default text");
Q preset2 = Q.preset().setTextAlign(Q.JUSTIFY).setPreset(preset1);
Q lblgrp = Q.label().setPreset(preset1).setText("graphic label text");
lblgrp.setTextAlign(Q.CENTER);
Q lbl = Q.label().setPreset(preset2).setText("label text").setGraphic(lblgrp).setTextAlign(Q.JUSTIFY);
Label lblfx = lbl.get(Label.class);
Button btnfx = Q.button().setGraphic(lblfx).get(Button.class);
Label lblgrpfx = lbl.get(Q.GRAPHIC, Label.class);
String lbltext = lbl.get(Q.TEXT, String.class);
Q.warp(btnfx).setStyle("-fx-background-color:red;").setText("this is a button");
```
