
# Components

Components are leaf node namespaces or directories.

![](../assets/components.png)
1. The files within BloodStats belong to the component *BloodStats*.
2. BodyStats.razor is an orphaned class (belonging to no component). This should be change be either moving all files in the namespace *BodyStats* or by moving BodyStats.razor into a components (e.g. Shared, Layout, ...)

> [!TIP] Make sure source code files reside only in leaf node namespaces or directories so that source code can always be identified within a specific component.

