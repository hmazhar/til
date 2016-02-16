# How to weld vertices based on a tolerance

Input: List of vertices, every three vertices is a unique triangle

Round vertices to a certain tolerance if needed

``` 
for (int i = 0; i < meshVertices.size(); i++) {
    meshVertices[i].x = std::round(meshVertices[i].x * 1000000) / 1000000.0;
    meshVertices[i].y = std::round(meshVertices[i].y * 1000000) / 1000000.0;
    meshVertices[i].z = std::round(meshVertices[i].z * 1000000) / 1000000.0;
}
``` 

Find unique vertices and gerenate triangle indices. Based on the weld vertices demo in thrust.
``` 
std::vector<chrono::real3> vertices = meshVertices;
thrust::sort(vertices.begin(), vertices.end());
vertices.erase(thrust::unique(vertices.begin(), vertices.end()), vertices.end());
thrust::lower_bound(vertices.begin(), vertices.end(), meshVertices.begin(), meshVertices.end(), meshIndices.begin());
meshVertices = vertices;
```

If writing as an obj file offset indices by 1

``` 
for (int i = 0; i < meshIndices.size(); i++) {
    meshIndices[i]++;
}
```