> [**StandardShader**](https://docs.unity3d.com/2021.1/Documentation/Manual/shader-StandardShader.html)

# 스탠다드 쉐이더 (Standard Shader)

---

> 유니티의 **Standard Shader**는 포괄적인 기능을 갖춘 내장형 쉐이더입니다.

Standard Shader는 돌, 나무, 유리, 플라스틱, 금속과 같은 "실제" 물체를 렌더링하는 데 사용할 수 있으며, 다양한 유형의 쉐이더와 조합을 지원합니다. 머터리얼의 텍스처 슬롯과 프로퍼티의 사용 여부에따라 특정 기능을 활성화하거나 비활성화할 수 있습니다.

![img](https://docs.unity3d.com/uploads/Main/Inspector-MaterialSimple.png)

또한 Standard Shader는 **Physcial Based Shading**이라는 고급 라이팅 모델을 포함하고 있습니다. Physcial Based Shading**(PBS)**는 머터리얼과 빛의 상호작용을 현실과 유사한 방식으로 시뮬레이션합니다. PBS는 최근에서야 실시간 그래픽이 가능해졌는데, 이 그래픽은 조명과 머터리얼이 직관적이고 현실적으로 함께 존재하는 상황에서 가장 잘 작동합니다.

PBS의 보완할 점이라면, 다른 조명이 비치는 상황에서도 일관되고 그럴듯한 외관을 얻을 수 있는 사용자 친화적인 방법을 만드는 것입니다. 이는 즉 실효성이 불확실한 여러 임시 모델을 사용하지 않고도 실제로 빛이 어떻게 작용하는지를 모델링하는 것입니다. 

그렇게 하기 위해 에너지 보존, 프레넬 반사, 그리고 '물체의 표면이 어떻게 가려지는지'[^1]를 포함한 물리학의 원리를 따릅니다.

> **에너지 보존**
> 물체는 받은 빛보다 더 많은 빛을 반사하지 않는다

> **프레넬 반사**
> 모든 표면은 그레이징 각도에서 반사가 더 잘 일어난다.

Standard Shader는 건축 자재로 알려진 단단한 표면을 렌더링 할 것을 예상하고서 설계했기 때문에 돌, 유리, 도자기, 황동, 은, 그리고 고무와 같이 현실에 존재하는 대부분의 물질들을 다룰 수 있습니다.

덧붙여 피부, 머리카락, 옷감과 같이 단단하지 않은 물질도 다룰 수 있게 될 것입니다.

![A scene rendered using the standard shader on all models](https://docs.unity3d.com/2021.1/Documentation/uploads/Main/StandardShaderIntroVikingScene.jpg)

Standard Shader를 사용하면, 다양한 유형의 쉐이더[^2]를 사용하는 대신에 하나의 쉐이더를 사용할 수 있게 됩니다. 이 경우 씬의 모든 영역에서 동일한 조명 계산이 사용되기 때문에, 이 쉐이더를 사용하는 모든 모델에 걸쳐 사실적이고, 일관적인 명암 분포를 제공받게 됩니다.

# 전문 용어

> 유니티에서 PBS에 대해 이야기할 때 매우 유용한 개념들이 많이 있습니다 : 

## 1. 에너지 보존

에너지 보존은 물체는 그 물체가 받은 빛 보다 더 많은 빛을 반사하지 않도록 보장하는 물리 기반의 개념입니다. 머터리얼의 Specular[^3]가 높을수록 확산이 적게 발생하며 표면이 매끄러울수록 하이라이트가 강해지고 작아집니다.

![The light rendered at each point on a surface is calculated to be the same as the amout of light received from its environment. The microfacets of rough surfaces are affected by light from a wider area. Smoother surfaces give stronger and smaller highlights. Point A reflects light from the source towards the camera. Point B takes on a blue tint from ambient light from the sky. Point C takes its ambient and reflective lighting from the surrounding ground colours.](https://docs.unity3d.com/2021.1/Documentation/uploads/Main/StandardShaderEnergyConservation.jpg)

물체 표면의 각 지점에서 렌더링되는 빛은 그 환경으로부터 전달받는 빛의 양과 동일하도록 계산됩니다. 거친 표면의 극소면[^4]은 더 넓은 영역의 빛에 의해 영향을 받고, 매끄러운 표면은 하이라이트가 더 강해지고 좁아집니다.

<span style="color:gray">점 A는 광원에서 카메라 쪽으로 빛을 반사하고, 점 B는 하늘로부터 파란 색조를 띠게 되며, 점 C는 주변 배경색으로부터 은은한 반사 조명을 나타냅니다.</span>

## 2. HDR (**High Dynamic Range**)

HDR은 흔히 0~1 범위를 벗어난 색상을 말합니다. 예를 들어, 태양은 파란 하늘보다 10배 더 밝을 수 있습니다. 자세한 내용은 Unity Manual의 [HDR](https://docs.unity3d.com/2021.1/Documentation/Manual/HDR.html)페이지를 참조하십시오.

![A scene using High Dynamic Range. The sunlight reflecting in the car window appears far brighter than other objects in the scene, because it has been processed using HDR](https://docs.unity3d.com/2021.1/Documentation/uploads/Main/GlowWithHdrAdjusted.jpg)

<span style="color:gray">HDR을 사용한 씬 입니다. 차량의 창문에서 반사되는 햇빛은 HDR을 이용해 처리했기 때문에 현장의 다른 오브젝트보다 훨씬 밝게 보입니다.</span>

---

[^1]: 원문 : how surfaces occlude themselves (what is called Geometry Term)
[^2]: Diffuse(확산), Specular(정반사), Bumped Specular(?), Reflective(반사)
[^3]: 정반사
[^4]: 極小面, microfacet

