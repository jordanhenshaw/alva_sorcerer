Make lights track 3D audio objects
============================================================================

.. figure:: ../source/_static/3d_audio.png
   :align: center
   :alt: 3D Audio
   :width: 700px

A helicopter flies into the theater from the rear of the house. You hear it moving and you see lights pointing at it, tracking it. It moves from one side of the house to the other, then makes its way onto the stage. Then you hear and seem to see it drop down onto the stage. The lights and sounds always stayed in perfect sync with each other. 

Without Sorcerer, creating that theatre magic would be prohibitively complex and simply impossible without a gargantuan time commitment. With Sorcerer, high schoolers can quickly program this after school (assuming the speakers are present). Simply use the sequencer audio panel and animation strips with motion paths to make a light track an “empty” over in 3D view.

This system can only (easily) render one 3D audio object at once, but directly connects it to lighting control, performance capture, robust animation controls, and the rest of Blender/Sorcerer. It provides real time feedback/monitoring by sending OSC to control faders on a sound mixer. To produce deliverables, it also uses a collection of duplicated sounds strips that each represent a speaker out in the auditorium. Sorcerer will adjust the volume of each sound strip according to the 3D audio object’s proximity to that speaker in 3D space. Each strip’s audio is then rendered out separately. All the sound files are then grouped into a single Qlab cue and each sound file is sent to a different speaker through Qlab (or another audio playback software capable of numerous different audio sends). Note: most versions of Qlab require activation for this to work. 

.. figure:: ../source/_static/3d_audio_panel.png
   :align: center
   :alt: 3D Audio Panel
   :width: 400px

First, set up your light and your speakers over in 3D view using Blender. Then, navigate to the sequencer to connect to the lighting and sound system. Create an animation strip and click the Motion Paths icon to the left of the pan/tilt values. Then, create an “empty” in 3D view for the mover to track. Use the tooltips and collapsible help section there to help you in this. Ensure the mover out on the rig properly tracks the empty in 3D view. Then create several duplicates of the sound file to be played. Each of these should start and end on the same frame. The first sound strip duplicate should be set on the Alva Sorcerer “Audio” tab (open and close this area with the N key) as a sound object. Link it to the empty. Then, set the other duplicate sound strips to link to the speakers you have placed in 3D space. Add OSC syntax to send to your sound mixing console if you wish to preview the sound effect live. You will need to turn on a looping sound effect or oscillator tone to hear the sound move throughout the room. As you move the empty around in the 3D space, you should see the read-only audio monitor change the volume levels of the speaker strips. However, the volume of those strips will not be affected yet. 

If you wish, you can use motion tracking/performance capture to drive this audio object using a single motion tracker and footage of a laser pointer moving around. 

When your 3D audio animation is complete, the volumes must be “baked” into the sound strip volumes to output the 3D audio rendering as deliverables using the bake button. Systems like Dolby Atmos produce single audio file deliverables that involve copious metadata, but Sorcerer instead outputs a multitude of extremely simple files, one for each speaker. That makes it difficult to quickly make spatial changes, but easy to understand and easy to prevent problems. To do this, “solo” each speaker sound strip, press the Export Channel button to pull up Blender’s mixdown window. 

In the future, this software will support multiple audio objects at the same time. It will hopefully also delete the practice of creating numerous duplicate audio strips since this will in the future be done all in the background. 

To ensure any lighting animations properly sync to the audio object, store the lighting animation directly onto the console with a qmeo.
