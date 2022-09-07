```python
import matplotlib.pyplot as plt
import numpy as np
import  mne
```


```python
from GetICCValues import GetICCValues
from dataFile import GetData
```


```python
allSubjectsIccValues = GetICCValues()
data = GetData()
```


```python
REFERENCE_NAME = 'averageReference'
FEATURE_NAME = 'AbsolutePowerFeature'
FEATURE_LIST = data.getFeatureList('AbsolutePowerFeature')
ELECTRODE_LIST = data.getElectrodeList()
EPOCH_LIST = data.getEpochList()
```


```python
numFeature = len(FEATURE_LIST)
numElectrode = len(ELECTRODE_LIST)
numEpoch = len(EPOCH_LIST)
```


```python
#epoch[featureList[electrodes]]]
iccValues = allSubjectsIccValues.getICCValues(FEATURE_NAME, REFERENCE_NAME)
```


```python
iccValues
```




    array([[[ 7.61518098e-03,  1.35192462e-02,  2.54741559e-02,
              2.56261315e-02,  2.23919524e-01,  2.93118180e-01,
              3.62541990e-01,  4.33290561e-01,  3.15017276e-02,
              6.04463324e-02,  1.16295493e-01,  1.30655938e-01,
              2.02405988e-02,  3.57886846e-02,  6.63350339e-02,
              7.45379439e-02,  1.45081202e-01,  2.58855021e-01,
              4.28775940e-01],
            [ 4.70954741e-01,  5.38461780e-03,  1.00036310e-02,
              1.88111271e-02,  1.64688628e-02, -4.32442613e-04,
             -1.18386815e-03, -2.87262493e-03, -9.04558658e-03,
              2.88628736e-01,  3.62000778e-01,  4.34548969e-01,
              5.07184157e-01,  3.66262680e-02,  6.33680471e-02,
              1.09524052e-01,  1.26893195e-01,  2.15550854e-02,
              3.74956748e-02],
            [ 6.49492594e-02,  6.62312820e-02,  5.85743525e-02,
              1.10090042e-01,  1.99697427e-01,  2.04355127e-01,
             -1.19381373e-03, -2.46478241e-03, -5.04531826e-03,
             -1.15275561e-02,  5.06764376e-01,  6.06268492e-01,
              6.86385976e-01,  7.57942293e-01,  2.62030908e-01,
              3.43806856e-01,  4.23594075e-01,  5.13980807e-01,
              1.17199293e-01],
            [ 1.61033521e-01,  2.50669758e-01,  3.35992410e-01,
              5.99587043e-01,  7.22562680e-01,  8.06886235e-01,
              8.65646926e-01,  1.45199110e-01,  2.13204254e-01,
              3.35177380e-01,  4.07758947e-01,  3.36875434e-01,
              4.53322979e-01,  5.83209805e-01,  6.91354036e-01,
              3.85862974e-01,  4.72672324e-01,  5.44612664e-01,
              6.20250143e-01],
            [ 3.50434003e-01,  4.37955748e-01,  5.13573837e-01,
              5.93052556e-01,  4.27031324e-02,  6.27581259e-02,
              9.30210988e-02,  1.39074364e-01,  1.84343588e-01,
              2.60429064e-01,  3.61467542e-01,  4.71016092e-01,
              5.78346911e-02,  9.26609286e-02,  1.45765022e-01,
              1.97344492e-01,  2.85684545e-01,  3.70421574e-01,
              5.02486839e-01],
            [ 6.01833497e-01,  1.86284073e-01,  2.54541831e-01,
              3.63858470e-01,  4.62673648e-01,  9.79814422e-02,
              1.36671895e-01,  2.03389141e-01,  2.91431133e-01,
              1.44095274e-01,  1.94809552e-01,  2.84600893e-01,
              3.68242797e-01,  2.43961575e-02,  4.47205348e-02,
              7.69506367e-02,  1.01064525e-01,  2.16336480e-01,
              3.22800505e-01]],
    
           [[ 4.75560443e-01,  5.98013469e-01,  2.78459701e-01,
              4.05576127e-01,  5.36922096e-01,  6.41421752e-01,
              1.66906651e-01,  2.40052910e-01,  3.17463762e-01,
              4.13630033e-01,  1.81537838e-01,  2.65342687e-01,
              3.56643652e-01,  4.72399294e-01, -1.36392684e-03,
             -2.88122907e-03, -5.98141656e-03, -1.23718995e-02,
              7.73156142e-04],
            [ 8.24104118e-04,  4.00810080e-05, -4.69662901e-03,
              1.19049976e-01,  1.78094236e-01,  2.67559577e-01,
              3.58072196e-01,  8.07314692e-02,  1.29859158e-01,
              2.03146000e-01,  2.81028629e-01,  3.76181147e-01,
              4.58428675e-01,  5.39070380e-01,  6.20009694e-01,
              3.83431229e-01,  4.67430568e-01,  5.50872276e-01,
              6.34167420e-01],
            [ 5.79085253e-02,  8.09131264e-02,  1.13758956e-01,
              1.63831562e-01,  2.27705648e-03,  3.74261404e-03,
              4.13177709e-03,  2.79103957e-03,  5.59439625e-03,
              9.68132234e-03,  1.73823222e-02,  2.09020615e-02,
              2.21551831e-01,  3.04297886e-01,  4.37126716e-01,
              5.32738180e-01,  3.97357072e-03,  4.86397903e-03,
              6.35024351e-03],
            [ 5.30803519e-03,  6.00796878e-03,  7.87190038e-03,
              1.07481658e-02,  1.21571516e-02, -1.28167161e-03,
             -2.73701885e-03, -5.62360257e-03, -1.17283284e-02,
              2.17675403e-03,  3.64722546e-03,  5.12013062e-03,
              7.66134555e-04,  1.56276944e-02,  2.63452501e-02,
              4.39200646e-02,  5.66746218e-02,  1.06910266e-01,
              1.60804417e-01],
            [ 2.47732284e-01,  3.36512125e-01,  2.13963348e-01,
              2.85880110e-01,  3.60841280e-01,  4.52275337e-01,
              2.28865551e-01,  3.07847973e-01,  3.86746748e-01,
              4.83345380e-01,  1.08606701e-02,  1.60653148e-02,
              2.40339025e-02,  3.56817510e-02,  2.63669693e-03,
              3.56574777e-03,  4.80392491e-03,  1.09998456e-03,
              6.54710205e-01],
            [ 7.56832099e-01,  8.49415938e-01,  8.94403091e-01,
              1.38217923e-01,  1.94408625e-01,  2.85300493e-01,
              3.86753802e-01,  3.11964733e-01,  3.97901445e-01,
              4.84439301e-01,  5.59179126e-01,  3.12807848e-01,
              4.04559613e-01,  4.96702994e-01,  5.75158721e-01,
              2.21446937e-02,  3.25302424e-02,  4.70915476e-02,
              6.46257414e-02]],
    
           [[ 1.10222602e-02,  1.74477183e-02,  2.93439750e-02,
              2.97508178e-02,  1.44621280e-01,  2.16010622e-01,
              3.11178429e-01,  3.75762161e-01,  2.36839336e-01,
              3.13320514e-01,  4.12118067e-01,  5.26326358e-01,
              9.96464455e-02,  1.32476906e-01,  1.87400962e-01,
              2.49319424e-01,  1.47650185e-01,  2.01798751e-01,
              2.69956879e-01],
            [ 3.43259856e-01,  2.48529876e-02,  3.72807871e-02,
              6.00196418e-02,  8.95212209e-02,  1.08737130e-02,
              1.24980120e-02,  1.89012969e-02,  2.79765967e-02,
              3.99268273e-01,  4.98698093e-01,  6.28396161e-01,
              6.47424252e-01,  1.83201382e-02,  2.83527156e-02,
              4.67931689e-02,  7.45443200e-02,  3.81220965e-01,
              4.71065800e-01],
            [ 5.55251286e-01,  6.20471197e-01,  3.21355568e-01,
              4.00614494e-01,  4.83902243e-01,  5.55551982e-01,
              1.32352055e-02,  1.94071063e-02,  3.09358968e-02,
              4.44712486e-02,  1.33890601e-01,  1.79192066e-01,
              2.34058437e-01,  3.17287959e-01,  6.71360375e-02,
              1.04434693e-01,  1.64239940e-01,  1.89320393e-01,
              2.47928306e-01],
            [ 3.31117796e-01,  4.43260378e-01,  5.78312976e-01,
              2.92333789e-02,  4.29459848e-02,  6.47008998e-02,
              9.10614164e-02,  9.19269172e-03,  1.36133537e-02,
              2.26726351e-02,  3.37757540e-02,  1.06921014e-01,
              1.58848920e-01,  2.41739501e-01,  3.41155012e-01,
              2.11194434e-02,  3.34927276e-02,  4.65617954e-02,
              6.24667619e-02],
            [ 7.32063018e-02,  7.82742097e-02,  7.98406873e-02,
              7.71852832e-02, -7.21075395e-04, -1.95040998e-03,
             -4.12486416e-03, -9.00618416e-03,  9.28928640e-02,
              1.36589491e-01,  1.98459178e-01,  2.60649291e-01,
              1.38170309e-01,  1.92825305e-01,  2.75742583e-01,
              3.67285650e-01,  4.15943495e-02,  6.42114261e-02,
              9.81939058e-02],
            [ 1.33219626e-01, -1.18942496e-03, -2.49854015e-03,
             -5.27296407e-03, -1.14929744e-02,  8.88848223e-03,
              1.48994674e-02,  2.46984656e-02,  2.65214577e-02,
              9.31044346e-02,  1.35058521e-01,  1.92337945e-01,
              2.82481673e-01,  3.26622081e-01,  4.20041662e-01,
              5.00336160e-01,  5.98034367e-01,  3.66181934e-01,
              4.66941609e-01]],
    
           [[ 5.46326948e-01,  6.46997061e-01,  6.76794473e-03,
              1.01473298e-02,  1.49986297e-02,  2.20089633e-02,
             -4.48057418e-04, -1.25585078e-03, -3.36153419e-03,
             -8.80955252e-03,  4.35676642e-01,  5.79659086e-01,
              6.96016421e-01,  7.59354078e-01,  1.28642017e-01,
              1.84540494e-01,  2.84861184e-01,  3.93358005e-01,
              6.03381924e-02],
            [ 9.06386431e-02,  1.35001713e-01,  1.99929741e-01,
              8.25735947e-02,  1.27926272e-01,  1.86998486e-01,
              2.83963494e-01,  5.67714811e-02,  8.51048076e-02,
              1.25783604e-01,  1.79098127e-01, -1.04188575e-03,
             -2.25435791e-03, -4.78973639e-03, -1.09533604e-02,
              9.91489095e-02,  1.48306570e-01,  2.04689402e-01,
              2.42820386e-01],
            [ 4.42881943e-02,  6.27769709e-02,  9.78769377e-02,
              1.41212857e-01,  3.46438745e-01,  4.37437290e-01,
              5.11807858e-01,  5.90522301e-01,  3.13723688e-01,
              3.99379787e-01,  4.71180819e-01,  5.54295759e-01,
              7.42091170e-02,  1.06145432e-01,  1.59183281e-01,
              2.33575563e-01,  7.50806165e-02,  1.20533035e-01,
              1.82717569e-01],
            [ 2.43558240e-01,  1.31110409e-01,  1.96000759e-01,
              3.02229978e-01,  3.75046380e-01,  2.92827184e-01,
              4.02746929e-01,  5.47937273e-01,  6.50644011e-01,
              3.54347667e-01,  4.68585722e-01,  5.81632919e-01,
              6.78076045e-01,  2.36329707e-01,  3.35006890e-01,
              4.29047310e-01,  5.40939951e-01,  2.14329655e-01,
              2.87800688e-01],
            [ 4.10231527e-01,  5.21955130e-01,  7.60774722e-02,
              1.18175633e-01,  1.86169447e-01,  2.60931547e-01,
              4.60937296e-01,  5.89586604e-01,  7.31399271e-01,
              8.05167795e-01,  2.73770573e-01,  3.97893689e-01,
              5.27577666e-01,  6.40579657e-01,  2.99093060e-01,
              3.73178919e-01,  4.59920534e-01,  5.30141130e-01,
              3.00718520e-01],
            [ 3.73848244e-01,  4.64223092e-01,  5.35970455e-01,
              1.94952662e-02,  2.72413504e-02,  4.08590478e-02,
              5.93139122e-02,  4.52704462e-03,  7.64727959e-03,
              1.32434851e-02,  1.07851215e-02,  3.77735641e-02,
              6.36625427e-02,  1.07123173e-01,  1.39669838e-01,
              2.12780607e-01,  2.96439940e-01,  4.15226391e-01,
              0.00000000e+00]]])




```python
mneInfo = mne.create_info(ch_names = ELECTRODE_LIST, ch_types = ['eeg'] * numElectrode, sfreq=250)
mneInfo.set_montage('standard_1020')
```




<table class="table table-hover table-striped table-sm table-responsive small">
    <tr>
        <th>Measurement date</th>

        <td>Unknown</td>

    </tr>
    <tr>
        <th>Experimenter</th>

        <td>Unknown</td>

    </tr>
        <th>Participant</th>

        <td>Unknown</td>

    </tr>
    <tr>
        <th>Digitized points</th>

        <td>0 points</td>

    </tr>
    <tr>
        <th>Good channels</th>
        <td>19 EEG</td>
    </tr>
    <tr>
        <th>Bad channels</th>
        <td>None</td>
    </tr>
    <tr>
        <th>EOG channels</th>
        <td>Not available</td>
    </tr>
    <tr>
        <th>ECG channels</th>
        <td>Not available</td>

    <tr>
        <th>Sampling frequency</th>
        <td>250.00 Hz</td>
    </tr>


    <tr>
        <th>Highpass</th>
        <td>0.00 Hz</td>
    </tr>


    <tr>
        <th>Lowpass</th>
        <td>125.00 Hz</td>
    </tr>


</table>




```python
fig, ax = plt.subplots(ncols=numEpoch, nrows=numFeature, figsize=(100, 100), gridspec_kw=dict(top=0.9),
                       sharex=True, sharey=True)

for epoch in range(0, numEpoch):
    epoch_num = EPOCH_LIST[epoch]
    for feature in range(0, numFeature):
        feature_name = FEATURE_LIST[feature]
        dataToPlot = iccValues[epoch][feature]
        mne.viz.plot_topomap(dataToPlot, mneInfo, axes = ax[feature][epoch], show = False)
        ax[feature][epoch].set_title([feature_name, epoch_num], fontweight='bold', fontsize=64)
```


    
![png](output_8_0.png)
    
