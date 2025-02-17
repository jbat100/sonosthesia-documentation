# Sonosthesia

This is the landing page for the Sonosthesia project. It gives a high level overview of the different components and planned evolutions. It is founded and principally driven by [Jonathan Thorpe](https://www.linkedin.com/in/jonathan-thorpe-811b845b/) inspired by an old vision of XR as an artistic audio/visual performance environment, the first draft of which dates back to [2013](https://github.com/jbat100/sonosthesia-website/blob/master/documents/VSC2013.pdf). After a long pause while working fulltime as software architect for no code XR creation tool [Minsar](https://www.opuscope.com/minsar/overview) and sadly seeing die due to lack of funds the time has come for a second draft with many lessons learned. Chief amongst these is the need to integrate within existing tech stacks rather than trying to replace them. 

## Summary

- A set of modular and reusable [Unity packages](https://github.com/jbat100/sonosthesia-unity-packages) covering a broad range of use cases related to audio visual interactive immersive art. These include data flow and processing, audio analysis, networking, MIDI/MPE, object interaction and manipulation, procedural shaders, meshes and VFX, and more. 
- A set of Unity demo applications which showcase package usage, some in tandem with running Ableton Live sessions. These include:
  - [MIDI/MPE connectivity](https://github.com/jbat100/sonosthesia-unity-demo-midi)
  - [Audio reactive procedural graphics](https://github.com/jbat100/sonosthesia-unity-demo-deform)
  - [Musical performance with bi-lateral Live/Unity communication](https://github.com/jbat100/sonosthesia-unity-demo-live)
  - [Reactive assets using FMOD](https://github.com/jbat100/sonosthesia-unity-reactive-assets) .
- A [pipeline for extracting audio analysis](https://github.com/jbat100/sonosthesia-audio-pipeline) ahead of time for static audio assets, and playing them back in Unity. This allows performance gains which are particularly crucial in XR apps. 
- A [node connector app](https://github.com/jbat100/sonosthesia-daw-connector) to ease bilateral communications with DAWs
- Max 4 Live [devices](https://github.com/jbat100/sonosthesia-daw-connector/tree/main/m4l) aiming to provide detailed state information, sound descriptors and powerful remote control opportunities.

# Ongoing Projects

## Reactive assets

Unity demo project [here](https://github.com/jbat100/sonosthesia-unity-reactive-assets). Videos with reactive sound available [here](https://www.youtube.com/watch?v=cWXSkkcUVtA&list=PL8HqVGO27FJP4i2wh5F9h6oP8IscdKsg2) and [here](https://www.youtube.com/watch?v=Pw_EPlO7XNs&list=PL8HqVGO27FJP4i2wh5F9h6oP8IscdKsg2). This demo brings together multiple aspects of the project, namely:

- Physics and and hand shape interaction using a custom affordance system
- Continuous data flow and processing to control graphics and sound using interaction data
- Advanced procedural graphics and sound techniques allowing performant real time control


<p align="center">
    <img alt="RtMIDIInput" src="https://github.com/user-attachments/assets/438dda8a-b4de-4131-9199-3ec0ecad2a4d" width="75%">
</p>

<p align="center">
    <img alt="RtMIDIInput" src="https://github.com/user-attachments/assets/f6a21a40-8e9c-4807-abb2-b38d2de29527" width="75%">
</p>

## Real time audio reactivity

Audio reactivity is a powerful mechanism which can bring life to a real time scene (XR or plain 3D), the core of the approach is to extract sound descriptors from sound in order to drive other aspects of the scene. These can be procedural graphics, shader or VFX parameters, procedural movement or physics, lighting or whatever the need might be. A number of different approaches are being investigated to ease this process:

- Accessing audio data for [AudioSource](https://docs.unity3d.com/ScriptReference/AudioSource.html) or [AudioListener](https://docs.unity3d.com/ScriptReference/AudioListener.html) and extracting energy in [octave bands](https://en.wikipedia.org/wiki/Octave_band). See [com.sonosthesia.audio](https://github.com/jbat100/sonosthesia-unity-packages/tree/main/packages/com.sonosthesia.audio/Runtime). This can be used for [timeline audio tracks](https://docs.unity3d.com/Packages/com.unity.timeline@1.8/manual/tl-overview.html) playing through AudioSource components.
- Extracting audio analysis ahead of time and saving on performance at runtime, using the [audio-pipeline](https://github.com/jbat100/sonosthesia-audio-pipeline) and playing them back on the unity timeline using custom [tracks and assets](https://blog.unity.com/engine-platform/extending-timeline-practical-guide).
- In the context of live musical performance using external DAWs such as Live or Logic Pro, audio analysis is performed in plugins (currently only implemented in Max 4 Live) and relayed to clients (currently Unity) using the [node connector app](https://github.com/jbat100/sonosthesia-daw-connector). This allows graphics to in real time to ongoing musical performances.
- (Planned) using core features of FMOD to run audio analysis on audio streams, allowing audio analysis to run on interactive audio which can be controlled by user interactions.
- (Planned) plugin into host system music playing apps and system sound to allow reactive visuals to be driven by user content. The feasability of on the fly source seperation (to isolate different instruments) will be investigated.


## Briding the gap from Game Engines to DAWs

While it's minimalist and old, MIDI is still the best option we have for controlling music software remotely. This option has been exploited by [Virtuoso-VR](https://virtuoso-vr.com/) and [MoveMusic](https://movemusic.com/) amongst others. Sonosthesia aims to expand the bridge, in particular exploiting the opportunities afforded by [Max 4 Live](https://www.ableton.com/en/live/max-for-live/) to allow more intricate bilateral interactions between XR controllers and music production software. This includes the DAWs broadcasting state which is not easly mapped to MIDI such as:

- Spectral analysis parameters.
- Currently playing clips.
- Automation curve values.
- Detailed transport and time signature.

A [demo app](https://github.com/jbat100/sonosthesia-unity-demo-live) is available and will be updated regularly

<p align="center">
    <img alt="Keyboard Builder" src="https://github.com/jbat100/sonosthesia-unity-demo-live/assets/1318918/7afd6093-199b-4bc8-8d21-d31f93ef32cf" width="75%">
</p>

<p align="center">
    <img alt="Keyboard Builder" src="https://github.com/jbat100/sonosthesia-unity-demo-live/assets/1318918/2a1deb74-3b2c-40eb-9a37-371e0db165d9" width="75%">
</p>

### Performance environment design

Building on the environment design tools knowledge acquired while working on [Minsar](https://www.opuscope.com/minsar/overview), Sonosthesia aims to provide useful generation tools for instruments such as keyboards, harps, xylophone, drum sets as well as more exotic forms afforded by the dematerialized nature of XR environments. These generation tools focus on:

- XR playability using controllers and hand tracking.
- Spatial and musical configurability (scale, sensitivity etc...).
- Real time channel and per note musical expression using mappings.
- Affordances providing real time visual and haptic feedback to increase presence.

<p align="center">
    <img alt="Keyboard Builder" src="https://github.com/jbat100/sonosthesia-unity-demo-instrument/assets/1318918/2a9622b9-c820-4f28-991e-22df35698778" width="75%"><
</p>

<p align="center">
    <img alt="Keyboard Builder" src="https://github.com/jbat100/sonosthesia-unity-demo-instrument/assets/1318918/3e62e079-c46d-4778-802b-14ba055adcef" width="75%">
</p>

### Tools for performance procedural graphics

Pushing the limits of procedural graphics within the constraints imposed by the high FPS required for smooth XR experience, Sonosthesia nourishes itself from the top content providers such as [Catlike Coding](https://catlikecoding.com/unity/tutorials/), [Keijiro](https://github.com/keijiro?tab=repositories), [Gabriel Aguiar](https://www.youtube.com/@GabrielAguiarProd) expanding on their spark while allowing intricate real time parameter control using sound descriptors or other signals. Avenues currently being investigated include:

- Exploring dynamic noise generators.
- Procedural shape fragment shaders with mapped parameters.
- VFX graphs with mapped parameters and event attributes.
- Procedural mesh generation and deformations using the Unity Job System.
- ECS based animations drivers.

A Unity [demo app](https://github.com/jbat100/sonosthesia-unity-demo-deform) demonstrates some of the techniques with results compiled in a YouTube [playlist](https://www.youtube.com/playlist?list=PL8HqVGO27FJP4i2wh5F9h6oP8IscdKsg2).

<p align="center">
  <img src="https://github.com/jbat100/sonosthesia-documentation/assets/1318918/34a5bd09-a028-4ff7-ac81-ba9cd99f952f" width="75%">
</p>

<p align="center">
  <img src="https://github.com/jbat100/sonosthesia-documentation/assets/1318918/8df2eefa-ad37-49bd-b48c-a6cf816dc609" width="75%">
</p>

<p align="center">
  <img src="https://github.com/jbat100/sonosthesia-unity-demo-deform/assets/1318918/9b2b6682-0e67-40b4-96fa-c3d0d54e1dbf" width="75%">
</p>

<p align="center">
  <img src="https://github.com/jbat100/sonosthesia-unity-demo-deform/assets/1318918/66ef7806-3d56-47c0-ba0f-db4ba7997a73" width="75%">
</p>

## Planned evolutions

### JUCE based audio plugins

Max 4 Live presents huge advantages in terms of processing and control possibilities as well as extermely fast iteration times. As such it is the perfect tool for experimentation, ideation and development. It has the massive drawback of only running in Ableton Live (and only the Max encompassing Suite version at that). As the tools and requirements mature, reviving old JUCE based [MIDI relay](https://github.com/jbat100/sonosthesia-relay) and [Audio Analysis](https://github.com/jbat100/sonosthesia-analyser) plugins to align with the evolving Sonosthesia protocols (based on OSC/UDP, websockets and MessagePack) will allow the same opportunities to be available on DAWs supporting VST and AU (as in all of them).

### Integrated sound synthesis

Remotely controlling sound synthesizer running within DAWs is very powerful and enabling for musicians and domain specialists but not an avenue for widespread public interest. In order for Sonosthesia to spread to a wider audience the sound generation mechanisms must run within the XR application itself. Sadly Unity has little to offer in this field, their [DSP graph](https://docs.unity3d.com/Packages/com.unity.audio.dspgraph@0.1/manual/index.html) has not evolved from its experimental stage. There are several avenues which can be explored to integrate the sound generation mechanisms into standalone apps with greater reach.

- Using FMOD with prebounced multilayered sonic hits and textures which can be modulated and mixed at runtime.
- Porting essential project components to Unreal Engines and using [MetaSounds](https://docs.unrealengine.com/5.1/en-US/metasounds-in-unreal-engine/) which contains enough sound synthesis building blocks to make a proper synthesizer without sinking all available project resources.
- Making an Apple/Unity hybrid app (a concept explored at length while working on [Wonderland](https://www.opuscope.com/wanderland/overview)) for Apple Vision Pro and using [Audio Kit](https://github.com/AudioKit/Cookbook) on the Apple side to handle sound synthesis. 
- Hoping that Unity give their developers some better tools to handle audio synthesis instead of relying on [Keijiro](https://github.com/keijiro?tab=repositories) to do all the work.


### Full blown audio visual compositions

Pulling together the different aspects of the project into standalone XR apps which adapt procedurally generated visuals to the users environment (using spatial mapping data), while using a mixture of baked and realtime interactive sonic generation to drive them is an exciting prospect. Reviving old electronic compositions such as [Starfall](https://soundcloud.com/jbat100/starfall) and [Eurus](https://soundcloud.com/jbat100/eurus) giving them an XR twist is on the TODO list. 

## Potential revenue streams

Currently the project is only driven by personal time and money investment from [Jonathan Thorpe](https://www.linkedin.com/in/jonathan-thorpe-811b845b/) which will only be sustainable for another year or two. Beyond that, revenue streams will be required for further work. A number of avenues are considered to generate them:

- A steady stream of cheap but non free XR apps containing audio visual compositions sold on app stores, similar to how consumers were once expected to buy audio tracks on music hosting websites before the days of streaming.
- Cooperations with XR studios wishing to enrich their productions with the intricate audio visual symbiosis offered by Sonosthesia, with dedicated support.
- Cooperations with music software companies wishing to provide inovating sound synthesis control mechanisms to their users, with XR instruments and control platforms tailored to specific instruments and racks.
- Government or industry funding opportunities will also be explored, they kept [Minsar](https://www.opuscope.com/minsar/overview) alive for a good few years so there is always some hope.
