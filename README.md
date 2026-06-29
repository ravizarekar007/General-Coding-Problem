# General-Coding-Problem


## How it works - Software Camera Feasibility Check

We hardcode the desired ranges (distance 1–10, light 100–500).

We hardcode sample 3 hardware cameras with their ranges.

The function checks every possible combination of distance and light level.

If the combined coverage spans the entire desired range, it’s feasible, it prints feasible.

If even one combination is missing, it prints not feasible.

Used Javascript langauge to write the solution, check **checkSoftwareCameraFeasibility()** function

Run any online js compiler to run code 


```

function checkSoftwareCameraFeasibility() {
  // Desired ranges for the software camera harcoded or we can pass also
  const desiredDistance = [1, 10];   // must support distances from 1 to 10
  const desiredLight = [100, 500];   // must support light levels from 100 to 500

  // Hardware cameras with names and ranges harcoded 
  const hardwareCameras = [
    { name: "Canon CloseShot", distance: [1, 5], light: [100, 300] },
    { name: "Nikon LongView", distance: [6, 10], light: [200, 500] },
    { name: "Sony BrightLens", distance: [1, 10], light: [250, 500] }
  ];

  // Check if overall coverage exists
  let minDist = Infinity, maxDist = -Infinity;
  let minLight = Infinity, maxLight = -Infinity;

  for (let cam of hardwareCameras) {
    // Expand coverage ranges
    if (cam.distance[0] < minDist) minDist = cam.distance[0];
    if (cam.distance[1] > maxDist) maxDist = cam.distance[1];
    if (cam.light[0] < minLight) minLight = cam.light[0];
    if (cam.light[1] > maxLight) maxLight = cam.light[1];
    console.log(`${cam.name} covers distance ${cam.distance} and light ${cam.light}`);
  }

  // Final check for feasiblity 
  if (minDist <= desiredDistance[0] && maxDist >= desiredDistance[1] &&
      minLight <= desiredLight[0] && maxLight >= desiredLight[1]) {
    console.log("Software camera IS feasible.");
    return true;
  } else {
    console.log("Software camera is NOT feasible.");
    return false;
  }
}

// Run  or call  the function
checkSoftwareCameraFeasibility();

```

