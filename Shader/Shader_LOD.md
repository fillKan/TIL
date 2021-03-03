# 쉐이더 LOD

쉐이더 Level of Detail (LOD)은 LOD값이 정해진 임계값 이하인 경우, 쉐이더 또는 서브 쉐이더를 사용합니다.

| LOD값 |                      대응되는 쉐이더                       |
| :---: | :--------------------------------------------------------: |
|  100  |                  VertexLit 종류의 쉐이더                   |
|  150  |                Decal, Reflective VertexLit                 |
|  200  |                          Diffuse                           |
|  250  | Diffuse Detail, Reflective Bumped Unlit, Reflective Bumped |
|  300  |                      Bumped, Specular                      |
|  400  |                      Bumped Specular                       |
|  500  |                          Parallax                          |
|  600  |                     Parallax Specular                      |

