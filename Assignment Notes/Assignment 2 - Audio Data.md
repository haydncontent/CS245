Assignment #2
CS 245, Spring 2026
Due Friday, January 23
I will give you the header file AudioData.h, which declares a class named AudioData as
well as some helper functions, used for manipulating audio data in floating point form. The
interface (public and private) of this class is
```

class AudioData {
public:
AudioData(unsigned nframes, unsigned R=44100, unsigned nchannels=1);
AudioData(const char *fname);
float sample(unsigned frame, unsigned channel=0) const;
float& sample(unsigned frame, unsigned channel=0);
float* data(void) { return &fdata[0]; }
const float* data(void) const { return &fdata[0]; }
unsigned frames(void) const { return frame_count; }
unsigned rate(void) const { return sampling_rate; }
unsigned channels(void) const { return channel_count; }
private:
std::vector<float> fdata;
unsigned frame_count,
sampling_rate,
channel_count;
};
void normalize(AudioData &ad, float dB=0);
bool waveWrite(const char *fname, const AudioData &ad, unsigned bits=16);
```

