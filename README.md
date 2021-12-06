# Local slip resistance

Here, we calculate the local slip resistance (LSR) of edge and screw dislocations on {110}, {112}, and {123} planes in CrMoNbTa, CrNbTaW, MoNbTaV, and MoNbTaW. LSR is just a name for the Peierls stress in MPEAs. For more information on LSR and Peierls stress, read [this paper](http://dx.doi.org/10.1016/j.actamat.2020.10.042). Since there are two types of dislocations, three types of planes, and four MPEAs, you need to prepare 24 directories on your local computer and on Pod, respectively.

## {110} LSR of the edge dislocation in CrMoNbTa

Take the {110} LSR of the edge dislocation in CrMoNbTa as an example. First, on your local computer, download the four files in CrMoNbTa/110-edge/ from this GitHub repository to a local directory `CrMoNbTa/110-edge`. These four files are

- `lmp_edge.batch`, which is for job submission
- `edge_CrMoNbTa_110_40nm_pad.lmp`, which is the LAMMPS data file
- `peierls_edge_pad_y_normal.in`, which is the LAMMPS input file
- `CrMoNbTaVW_Xu2022.eam.alloy`, which is an interatomic potential file made by [Xu et al.](http://dx.doi.org/10.1016/j.commatsci.2021.110942)

Then on Pod, create a new directory in your `$HOME`. Say the directory is also `CrMoNbTa/110-edge`. The commands are

`mkdir CrMoNbTa`

`cd CrMoNbTa`

`mkdir 110-edge`

`cd 110-edge`

Then upload, via Filezilla, the four files from your local computer to `110-edge` on Pod.

### One {110} edge LSR value in CrMoNbTa

In your terminal emulator, submit the job by typing

`sbatch lmp_edge.batch`

then hit Return. Then following [these procedures](https://github.com/shuozhixu/LAMMPSatUCSB/#LSR) to obtain the LSR value. Write it down.


### More {110} edge LSR values in CrMoNbTa

So far you have obtained one {110} edge LSR value, but for MPEAs, multiple LSR values exist even for the same type of dislocation on the same type of slip plane. It is suggested that 20 LSR values be calculated for the {110} edge dislocation. To calculate another LSR value, in your terminal emulator, go to the `110-edge` directory, edit the LAMMPS input file `peierls_edge_pad_y_normal.in`. In lines 18, 19, and 20, there are three random number seeds `1239`, `3534`, `4678`, respectively. Change any of the seeds to another integer, e.g., `6873`. For more information, please refer to [this page](https://lammps.sandia.gov/doc/set.html).

Then resubmit the job. Once it is finished, follow the same procedure to obtain another LSR value. Write it down.

Repeat the steps above 18 more times. Each time, change at least one random seed before you resubmit the job. Eventually, you will get 20 {110} edge LSR values. Calculate the mean and standard deviation of these 20 values.

## {110} LSR of the screw dislocation in CrMoNbTa

Repeat the steps above to get 20 {110} screw LSR in CrMoNbTa. Instead of CrMoNbTa/110-edge/ in this GitHub repository, you will need the files in CrMoNbTa/110-screw/. Note that some file names are slightly different from those for the edge dislocation. Once you have all LSR values, calculate their mean and standard deviation.

## {112} LSR and {123} LSR in CrMoNbTa

Repeat the steps above to get 20 {112} edge LSR, 20 {112} screw LSR, 20 {123} edge LSR, and 20 {123} screw LSR in CrMoNbTa. Instead of CrMoNbTa/110-XXX/ in this GitHub directory, you will need the files in CrMoNbTa/112-XXX/ and CrMoNbTa/123-XXX/. Again, calculate mean and standard deviation of:

- 20 {112} edge LSR
- 20 {112} screw LSR
- 20 {123} edge LSR
- 20 {123} screw LSR

## LSR in CrNbTaW

Repeat the steps above to get 20 {110} edge LSR, 20 {110} screw LSR, 20 {112} edge LSR, 20 {112} screw LSR, 20 {123} edge LSR, and 20 {123} screw LSR in CrNbTaW. Go to the six subdirectories under CrNbTaW/ in this GitHub repository. Obtain the mean and standard devitaion of each set of LSR.

## LSR in MoNbTaV

Repeat the steps above to get 20 {110} edge LSR, 20 {110} screw LSR, 20 {112} edge LSR, 20 {112} screw LSR, 20 {123} edge LSR, and 20 {123} screw LSR in MoNbTaV. Go to the six subdirectories under MoNbTaV/ in this GitHub repository. Obtain the mean and standard devitaion of each set of LSR.

Note: the interatomic potential file for this MPEA is different from that for the other three MPEAs.

## LSR in MoNbTaW

Repeat the steps above to get 20 {110} edge LSR, 20 {110} screw LSR, 20 {112} edge LSR, 20 {112} screw LSR, 20 {123} edge LSR, and 20 {123} screw LSR in MoNbTaW. Go to the six subdirectories under MoNbTaW/ in this GitHub repository. Obtain the mean and standard devitaion of each set of LSR.

## Results

Eventually, you will have 20 x 3 x 4 x 2 = 480 LSR values. You will also have 3 x 4 x 2 = 24 different mean and standard deviation of LSR.

## References

If you use the interatomic potential file from this GitHub repository, please cite

- Shuozhi Xu, Saeed Zare Chavoshi, Yanqing Su, [On calculations of basic structural parameters in multi-principal element alloys using small atomistic models](http://dx.doi.org/10.1016/j.commatsci.2021.110942), Comput. Mater. Sci. 202 (2022) 110942

If you use any other files from this GitHub repository, please also cite

- Rebecca A. Romero, Shuozhi Xu, Wu-Rong Jian, Irene J. Beyerlein, C.V. Ramana, [Atomistic calculations of the local slip resistances in four refractory multi-principal element alloys](http://dx.doi.org/10.1016/j.ijplas.2021.103157), Int. J. Plast. 149 (2022) 103157
- Shuozhi Xu, Yanqing Su, Wu-Rong Jian, Irene J. Beyerlein, [Local slip resistances in equal-molar MoNbTi multi-principal element alloy](http://dx.doi.org/10.1016/j.actamat.2020.10.042), Acta Mater. 202 (2021) 68--79