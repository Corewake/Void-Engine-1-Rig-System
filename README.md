Void Engine V1 Documentation

Engine Version: Void Engine V1
Unity Version: 6.0
Author: Corewake Studios
Last Updated: October 2025

Overview

Void Engine V1 is the custom physics and interaction system fully integrated into the Project Null player rig. All player movement, physics, and object interactions are managed directly by the rig’s two core scripts along with supporting hand and head scripts.

This setup provides:

Smooth, unified player physics

Realistic grabbing, throwing, and dual hand object manipulation

Stable body grounding, movement, and collision handling

A foundation for additional interactable assets such as a fully physics door and a moving platform

The rig also includes XR interaction presets and three friction presets for physics tuning.

Player Rig Structure

XR Origin Components: XR Origin

Input Action Manager

Rigidbody

Player Rig Core Scripts: 
PhysicRig.cs (handles body collider, player height adjustments, and updates the configurable joints on head and hands)

ContinuousMovementPhysics.cs (handles locomotion, rotation, jumping, and physics based movement)

Hand Components (Left & Right):

Rigidbody

Configurable Joint

GrabPhysics.cs (manages grabbing objects with physics based attachment using a FixedJoint)

Head Components:

Rigidbody

Configurable Joint

Additional Assets (Optional in Scene):

Fully physics door

Moving platform (has its own script with 2 points)

XR interaction presets and three friction presets

Script Overview

PhysicRig.cs:

Updates body collider height based on player head position

Updates configurable joints for head and hands to match controller transforms

Maintains stable physics connections between player rig components

ContinuousMovementPhysics.cs:

Handles movement and rotation using input actions

Supports jumping (both standard and hand velocity based)

Checks grounding via SphereCast against a ground layer

Moves and rotates Rigidbody using physics for smooth player control

Key Inspector Fields for ContinuousMovementPhysics.cs:

speed (movement speed)

turnSpeed (rotation speed)

jumpHeight (maximum jump height)

onlyMoveIfGrounded (restricts movement to grounded state)

jumpWithHand (enables hand powered jumping)

Input action fields for movement, turn, and jump

References to Rigidbody for body and hands

Ground layer mask and body collider reference

GrabPhysics.cs:

Handles object grabbing via physics

Uses FixedJoint to attach nearby Rigidbody when grab input is pressed

Releases the object when input is released

Radius and grab layer are configurable

Usage & Workflow

Import the Rig: Drag the player rig prefab into your scene. Ensure all hand and head rigidbodies, joints, and scripts are attached. (Should be by default)

Assign Input Actions: Configure move, turn, jump, and grab actions for the rig and hands.

Test Movement & Interaction:

Check standard movement, rotation, and jumping

Test grabbing objects using GrabPhysics

Experiment with Additional Assets: Physics door and moving platform can be used to test interaction fidelity.

Tuning: Use friction presets and inspector values to adjust movement, grab strength, and jump responsiveness.

Documentation Reference: Review this Google Doc for guidance on all inspector settings, physics behavior, and debugging tips.
Notes & Best Practices

The player rig is fully self contained; do not attach additional physics scripts if you don't know what your doing.

FixedUpdate is used for physics updates; keep the Fixed Timestep at 0.02 for stability.

Rigidbody should only exist on body, hands, and head - the rig manages all forces internally.

XR interaction presets are included and should be added to the scene to ensure proper controller mapping.

Any custom interactable objects should use Rigidbody components and colliders for physics compatibilit
