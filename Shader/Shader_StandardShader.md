> [**StandardShader**](https://docs.unity3d.com/2021.1/Documentation/Manual/shader-StandardShader.html)

# 스탠다드 쉐이더 (Standard Shader)

---

> 유니티의 **Standard Shader**는 포괄적인 기능을 갖춘 내장형 쉐이더입니다.

돌, 나무, 유리, 플라스틱, 금속과 같은 "실제" 물체를 렌더링하는 데 사용할 수 있으며, 다양한 쉐이더 유형과 조합을 지원합니다. 머터리얼의 다양한 텍스처 슬롯과 프로퍼티를 사용하거나 사용하지 않는 것만으로 특정 기능을 활성화하거나 비활성화할 수 있습니다.

![img](https://docs.unity3d.com/uploads/Main/Inspector-MaterialSimple.png)

또한 Standard Shader는 **Physcial Based Shading**이라는 고급 라이팅 모델을 포함하고 있습니다. Physcial Based Shading**(PBS)**는 머터리얼과 빛의 상호작용을 현실과 유사한 방식으로 시뮬레이션합니다. PBS는 최근에서야 실시간 그래픽이 가능해졌습니다. 이 실시간 그래픽은 조명과 머터리얼이 직관적이고 현실적으로 함께 존재하는 상황에서 가장 잘 작동합니다.

PBS의 보완할 점이라면, 다른 조명에서도 일관되고 그럴듯한 외관을 얻을 수 있는 사용자 친화적인 방법을 만드는 것입니다. 이는 효과가 있을 수도 없을 수도 있는 여러 임시 모델을 사용하지 않고도 실제로 빛이 어떻게 작용하는지를 모델링하는 것입니다. 

그렇게 하기 위해서 에너지 보존, 프레넬 반사, 그리고 평면을 가로막는 방법을 포함한 물리학의 원리를 따릅니다.

> **에너지 보존**
> 물체가 받은 빛보다 더 많은 빛을 반사하지 않는다

> **프레넬 반사**
> 모든 표면은 그레이징 각도에서 더 잘 반사된다.

> **평면을 가로막는 방법**
> Geometry Term, https://youtu.be/il0EJrY64qE?t=252