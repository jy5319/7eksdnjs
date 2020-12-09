# 7eksdnjs
import numpy as np
import matplotlib.pyplot as plt
from scipy import signal
import sk_dsp_comm.fir_design_helper as fir_d


hn=fir_d.fir_remez_lpf(1/8,1/6,100,0)
nf,hr=signal.freqz(hn)
Hr_dB=20*np.log10(abs(Hr))

n=np.arange(53)
plt.subplot(3,1,1); plt.stem(n,hn,"b"); plt.xlim(0,52); plt.grid();
plt.ylabel("h(n)"); plt.title("Impulse Responmse")
plt.subplot(3,1,2); plt.plot(nf/np.pi,Hr_dB,"b"); plt.xlim(0,1); plt.grid()
plt.ylim(-70,10); plt.title("Frequency Response"); plt.ylabel("Magnitude [dB]")

t=np.linspace(0,1,5000)
tn=chirp(t,f0=10, t1=0.2, f1=1000, method="linear")
yn=np.convolve(hn,tn)
plt.subplot(3,1,3); plt.plot(yn,"b"); plt.title("Frequency filtering result")
plt.xlabel("Samples(Frequency(0~1000[Hz]))"); plt.xlim(0,5000); plt.grid()
