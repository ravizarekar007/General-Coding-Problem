# General-Coding-Problem


## How it works - Software Camera Feasibility Check

We hardcode the desired ranges (distance 1–10, light 100–500).

We hardcode sample 3 hardware cameras with their ranges.

The function checks every possible combination of distance and light level.

A check for distance coverage & check for light coverage, it’s feasible, it prints feasible.

If even one combination is missing, it prints not feasible.

Used Javascript langauge to write the solution, check **checkSoftwareCameraFeasibility()** function

Run any online js compiler to run code 


```

function checkSoftwareCameraFeasibility() {
  // Desired ranges for the software camera are hracoded/ we can pass also
  const desiredDistance = [1, 10];   // must support distances from 1 to 10
  const desiredLight = [100, 500];   // must support light levels from 100 to 500

  // Hardware cameras with names and ranges
  const hardwareCameras = [
    { name: "Canon CloseShot", distance: [1, 5], light: [100, 300] },
    { name: "Nikon LongView", distance: [6, 10], light: [200, 500] },
    { name: "Sony BrightLens", distance: [1, 10], light: [250, 500] }
  ];

  // Print each camera’s coverage
  for (let cam of hardwareCameras) {
    console.log(`${cam.name} covers distance ${cam.distance[0]}–${cam.distance[1]} and light ${cam.light[0]}–${cam.light[1]}`);
  }

  // Step 1: Check distance coverage
  let minDist = Infinity;
  let maxDist = -Infinity;

  for (let cam of hardwareCameras) {
    if (cam.distance[0] < minDist) {
      minDist = cam.distance[0];
    }
    if (cam.distance[1] > maxDist) {
      maxDist = cam.distance[1];
    }
  }

  if (minDist <= desiredDistance[0] && maxDist >= desiredDistance[1]) {
    console.log(">✅ Distance range is fully covered.");
  } else {
    console.log(">❌ Distance range is NOT fully covered.");
    console.log("Software camera is NOT feasible.");
    return false;
  }

  // Step 2: Check light coverage
  let minLight = Infinity;
  let maxLight = -Infinity;

  for (let cam of hardwareCameras) {
    if (cam.light[0] < minLight) {
      minLight = cam.light[0];
    }
    if (cam.light[1] > maxLight) {
      maxLight = cam.light[1];
    }
  }

  if (minLight <= desiredLight[0] && maxLight >= desiredLight[1]) {
    console.log(">✅Light range is fully covered.");
  } else {
    console.log(">❌Light range is NOT fully covered.");
    console.log("Software camera is NOT feasible.");
    return false;
  }

  // Final result to check
  console.log("Software camera IS feasible with the given hardware cameras.");
  return true;
}

// Run or call the function
checkSoftwareCameraFeasibility();

```

