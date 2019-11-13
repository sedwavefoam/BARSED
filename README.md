# BARSED
SedWaveFoam case setup for sheet flow driven by velocity and acceleration skewed near-breaking waves on a sandbar
(BARSED, details of physical experiment refer to Mieras et al., 2019, JGR:Oceans, https://doi.org/10.1029/2018JC014564)
Modeling paper is published in Coastal Engineering (Kim et al., 2019, https://doi.org/10.1016/j.coastaleng.2019.103526)

### How to Simulate
* (1) FoamClearPolyMesh
* (2) blockMesh
* (3) snappyHexMesh -overwrite (If you want to skip the mesh refinement near the sediment pit, you can ignore this part)
* (4) extrudeMesh (This is to remove the redundant spanwise grids as an outcome of snappyHex)
* (5) go to 0 folder and make non-org files <br />
cp -r alpha.water.org alpha.water <br />
cp -r alpha.org alpha <br />
cp -r gamma.org gamma <br />
* (6) setWaveField (to fill the water, in default waves2Foam searches alpha.water and U)
* (7) copy U to Ub & alpha.water to alpha1 (SedWaveFoam uses alpha1) <br />
cp -r U Ub <br />
cp -r alpha.water alpha <br />
* (8) funkySetFields -time 0 (to fill up the sediment and remove that portion in alpha1)
* (9) SedWaveRANSDEVFoam (you can make the parallel if you want)
