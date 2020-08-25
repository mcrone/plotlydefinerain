# Plotly and python implementation of define the rain
http://definetherain.org.uk/

# Instructions for use

## Running ddPCR and export of files
First run the ddPCR reactions using the BioRad QX200 machine and QuantaSoft™ software. Then export the Amplitude and Cluster Data to a .csv file. Place these files into a separate folder.

## Kmeans clustering
The software then creates a dataframe from all amplitude data. The user must then select a well that will be used to generate the clusters (a positive control that doesn't have 100% positive droplets)

``` npposcontrol = df.loc[df['Sample'] == 'D02']['Ch1 Amplitude'].values ```

After clustering the positive and negative cluster are used to generate positive and negative thresholds. The positive threshold is 3 standard deviations lower than the mean of the positive cluster. The negative threshold is 3 standard deviations higher than the mean of the negative cluster. Anything that is found between the two thresholds is call droplet rain.

## Diagram and table generation
Finally, a plotly table and diagram are generated from the amplitude data.
