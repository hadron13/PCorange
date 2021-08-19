# Audio (caudio.h, assets/music.h, assets/sound.h)
## Basic Audio layer.

## Currently only plays flat sounds.
## No support for source manipulation.
## "Could do with some more love." - orangeduck  

# **types**:
* sound
* music
# **enumerations**:


# **constants**:


# **functions**:
## categories:

### **initialization/finalization**:
* **void audio_init()** - initialize audio layer
* **void audio_finish()** - shutdown audio layer and cleanup

### **sounds**:

* **int audio_sound_play(sound\* s, int loops)** - play a sound, return channel
* **void audio_sound_pause(int channel)** - pause a sound in a channel
* **void audio_sound_resume(int channel)** - resume a sound in a channel
* **void audio_sound_stop(int channel)** - stop a sound in a channel

* **sound\* wav_load_file(char\* filename)** - load sound from wave file
* **void sound_delete(sound\* s)** - delete sound

* **int sound_play(sound\* s)** - play sound, return the channel
* **int sound_play_looped(sound\* s, int loops)** - play sound looped, return the channel

* **int sound_play_at(sound\* s, vec3 pos, vec3 cam_pos, vec3 cam_dir)** - play sound in a space
* **int sound_play_at_looped(sound\* s, vec3 pos, vec3 cam_pos, vec3 cam_dir, int loops)** play sound looped in a space

### **music**:
* **void audio_music_play(music\* m)** - play a music
* **void audio_music_pause()** - pause the music
* **void audio_music_resume()** - resume the music
* **void audio_music_stop()** - stop the music

* **void audio_music_set_volume(float volume)** - set music volume, ranges from 0.0f to 1.0f
* **float audio_music_get_volume()** - get music volume

* **music\* mp3_load_file(char\* filename)** - load music from mp3 file
* **music\* ogg_load_file(char\* filename)** - load music from ogg file
* **void music_delete(music\* m)** - delete music






