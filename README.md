mc_triorb_description
==

URDF description of the **TriOrb** omnidirectional mobile base.

The base is modelled as a fixed `world` root carrying the body through three
actuated joints:

| Joint      | Type       | Axis      |
|------------|------------|-----------|
| `base_x`   | prismatic  | world `x` |
| `base_y`   | prismatic  | world `y` |
| `base_yaw` | continuous | world `z` |

The fixed link `mount` is where the UR5e `base_link` sits on CallM (15 mm along base +y, turned +90 deg),
and the RSDF surface `Base` has the same pose. The base mass and inertia come from the CallM MuJoCo model.

Layout
--

```
urdf/triorb.urdf   # the robot description
```

Building / installing
--

This is a standard mc_rtc-style description package: building and installing it
makes it discoverable through CMake's `find_package(mc_triorb_description)` (used
by `mc_rtc`'s `find_description_package` macro), and installs the URDF under
`share/.../mc_triorb_description/urdf/`.

```bash
# Standalone (no ROS)
cmake -S . -B build -DDISABLE_ROS=ON -DCMAKE_INSTALL_PREFIX=<prefix>
cmake --build build --target install

# Or, inside a ROS 1/2 workspace, build it like any other package (catkin / colcon).
```

The companion robot module that loads this description lives in
[`mc_triorb_module`](../mc_triorb_module).
