# General-Coding-Problem
Software Camera Feasibility Check

# How it works

We hardcode the desired ranges (distance 1–10, light 100–500).

We hardcode two hardware cameras with their ranges.

The function checks every possible combination of distance and light level.

If all combinations are covered by at least one hardware camera, it prints feasible.

If even one combination is missing, it prints not feasible.

Used Javascript langauge to write the solution, check **checkSoftwareCameraFeasibility()** function

Run any online js compiler to run code 


```
function checkSoftwareCameraFeasibility() {
  // Desired ranges for the software camera
  const desiredDistance = [1, 10];   // must support distances from 1 to 10
  const desiredLight = [100, 500];   // must support light levels from 100 to 500

  // Hardware cameras with their ranges
  const hardwareCameras = [
    { distance: [1, 5], light: [100, 300] },
    { distance: [6, 10], light: [200, 500] }
  ];

  // Simple check: go through each required distance and light level
  for (let dist = desiredDistance[0]; dist <= desiredDistance[1]; dist++) {
    for (let light = desiredLight[0]; light <= desiredLight[1]; light++) {
      let covered = false;

      // See if any hardware camera covers this point
      for (let cam of hardwareCameras) {
        if (
          dist >= cam.distance[0] && dist <= cam.distance[1] &&
          light >= cam.light[0] && light <= cam.light[1]
        ) {
          covered = true;
          break;
        }
      }

      // If no camera covers this combination, fail immediately
      if (!covered) {
        console.log("Software camera is NOT feasible.");
        return false;
      }
    }
  }

  console.log("Software camera IS feasible.");
  return true;
}

// Run the function
checkSoftwareCameraFeasibility();

```

