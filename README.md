# Sonosthesia

This is the landing page for the Sonosthesia project. It gives a high level overview of the different components and planned evolutions. It is founded and principally driven by [Jonathan Thorpe](https://www.linkedin.com/in/jonathan-thorpe-811b845b/) inspired by an old vision of XR as an artistic audio/visual performance environment, the first draft of which dates back to [2013](https://github.com/jbat100/sonosthesia-website/blob/master/documents/VSC2013.pdf). After a long pause while working fulltime as software architect for no code XR creation tool [Minsar](https://www.opuscope.com/minsar/overview) and sadly seeing die due to lack of funds the time has come for a second draft with many lessons learned. Chief amongst these is the need to integrate within existing tech stacks rather than trying to replace them. 

## Ongoing Projects

Currently, active development is focused on:

- A [node connector app](https://github.com/jbat100/sonosthesia-daw-connector) to ease bilateral communications with DAWs
- Max 4 Live devices aiming to provide detailed state information, sound descriptors and powerful remote control opportunities
- A set of modular and reusable [Unity packages](https://github.com/jbat100/sonosthesia-unity-packages)
- A set of Unity demo applications which showcase system usage, often in tandem with running Ableton Live sessions.


### Briding the gap from Game Engines to DAWs

While it's minimalist and old, MIDI is still the best option we have for controlling music software remotely. This option has been exploited by [Virtuoso-VR](https://virtuoso-vr.com/) and [MoveMusic](https://movemusic.com/) amongst others. Sonosthesia aims to expand the bridge, in particular exploiting the opportunities afforded by [Max 4 Live](https://www.ableton.com/en/live/max-for-live/) to allow more intricate bilateral interactions between XR controllers and music production software. This includes the DAWs broadcasting state which is not easly mapped to MIDI such as:

- Spectral analysis parameters 
- Currently playing clips
- Automation curve values
- Detailed transport and time signature

### Performance environment design

Building on the environment design tools knowledge acquired while working on [Minsar](https://www.opuscope.com/minsar/overview), Sonosthesia aims to provide useful generation tools for instruments such as keyboards, harps, xylophone, drum sets as well as more exotic forms afforded by the dematerialized nature of XR environments. These generation tools focus on:

- XR playability using controllers and hand tracking
- Spatial and musical configurability (scale, sensitivity etc...)
- Real time channel and per note musical expression using mappings
- Affordances providing real time visual and haptic feedback to increase presence

### Tools for creating immersive audio visual art

Pushing the limits of procedural graphics within the constraints imposed by the high FPS required for smooth XR experience, Sonosthesia nourishes itself from the top content providers such as [Catlike Coding](https://catlikecoding.com/unity/tutorials/), [Keijiro](https://github.com/keijiro?tab=repositories), [Gabriel Aguiar](https://www.youtube.com/@GabrielAguiarProd) expanding on their spark while allowing intricate real time parameter control using sound descriptors or other signals. Avenues currently being investigated include:

- Exploring dynamic noise generators 
- Procedural shape fragment shaders with mapped parameters
- VFX graphs with mapped parameters and event attributes 
- Procedural mesh generation and deformations using the Unity Job System
- ECS based animations drivers

A Unity [demo app](https://github.com/jbat100/sonosthesia-unity-demo-deform) demonstrates some of the techniques with results compiled in a YouTube [playlist](https://www.youtube.com/playlist?list=PL8HqVGO27FJP4i2wh5F9h6oP8IscdKsg2).

## Planned evolutions

### JUCE based audio plugins

### Integrated sound synthesis

Remotely controlling sound synthesizer running within DAWs is very powerful and enabling for musicians and domain specialists but not an avenue for widespread public interest. In order for Sonosthesia to spread to a wider audience the sound generation mechanisms must run within the XR application itself. Sadly Unity has little to offer in this field, their [DSP graph](https://docs.unity3d.com/Packages/com.unity.audio.dspgraph@0.1/manual/index.html) has not evolved from its experimental stage. 



### Full blown audio visual compositions



## Potential revenue streams

Currently the project is only driven by personal time and money investment from [Jonathan Thorpe](https://www.linkedin.com/in/jonathan-thorpe-811b845b/) which will only be sustainable for another year or two. Beyond that, revenue streams will be required for further work 
