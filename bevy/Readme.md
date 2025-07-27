

### Require Attribute

In Bevy, the #[require] attribute is used to declare that a particular component depends on the presence of another component on the same entity. When an entity is spawned with a component that has a #[require] attribute, Bevy automatically ensures that the required component is also present on that entity.
How it works:

• Declaration: You add #[require(OtherComponent)] to the #[derive(Component)] attribute of your component. For example:

    #[derive(Component)]
    #[require(Transform)]
    struct MyVisualComponent;

This states that MyVisualComponent requires Transform to be present on the same entity.

• Automatic Insertion: When you spawn an entity with MyVisualComponent, Bevy will automatically check if Transform is already present. If not, Bevy will insert Transform onto the entity.
• Default Values: If the required component implements Default, Bevy will insert a default instance of that component. You can also provide a custom constructor function within the #[require] attribute if the component doesn't implement Default or if you need specific initialization logic.

Purpose:

• Enforcing Invariants: #[require] helps enforce relationships and dependencies between components, ensuring that an entity always has the necessary components for a particular functionality to work correctly.
• Simplifying Entity Creation: It reduces the boilerplate of manually adding all dependent components when creating entities, especially for common patterns like a Camera3d component implicitly requiring Camera and Transform.

Important Considerations:

• Recursive Dependencies: #[require] dependencies are recursive, meaning if ComponentA requires ComponentB, and ComponentB requires ComponentC, then spawning an entity with ComponentA will also ensure ComponentC is present.
• Initialization: Be mindful of how required components are initialized, especially if they don't have a Default implementation or if custom initialization is needed.
• Runtime vs. Compile-time: Currently, #[require] primarily handles runtime insertion. There are ongoing discussions and proposals within the Bevy community to explore compile-time checks for required components within bundles.
