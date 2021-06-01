WPF-Basic
===
Resource
---
Resource는 두가지 종류로 나뉜다. Statistic Resource와 Dynamic Resource로 구분된다. 
Code에서는 Resource의 Dictionary를 통해 접근할 수 있다.(Resource["name"])   
+ Implied Resource
    + defined in Compile Time
+ Explicit Resource
    + defined in Runtime
   
Style
---
Resource에서 정의되며 Implied Style와 Explicit Style로 구분(Key의 유무)된다.
+ Implied Style
    + TargetType을 통해 대상을 한정한다. Type에 전체적으로 적용된다.
+ Explicit Style
    + Key를 통해 대상을 한정한다. Key를 가지고 있는 Element만 적용된다.
*다른 방식으로 개별 Element에만 속성을 정의하는 방식이 있다. Elements.Style을 사용하는 것이다.

Inheritance - Key를 통해 정의된 Style을 다른 스타일에서 상속하는 것. BasedOn을 사용한다.
   
Trigger - Style.Triggers로 하위 태그로서 사용된다. 어떤 조건(Condition)이 만족되면 Setter를 통해 Property의 값을 수정한다.
   
Style Structure
+ Resource
    + Style(TargetType, Key, BaseOn)
        + Setter(Property, Value)
        + Style.Triggers
            + Trigger(Condition, Value : Condition)
                + Setter(Property, Value : If Condition is satisfied then Set Property's Value)

Trigger 또한 3가지 종류로 Property, Data, Event Trigger가 있다.
+ Property Trigger
    + Condition이 Property로 Property를 인식하여 Trigger를 동작한다.
+ Data Trigger
    + Condition에 Data를 Binding하여 그 Value에 따라 Trigger를 동작한다.
    + DataTrigger Binding={Binding ElementName=name, Path=membername} Value=""
+ Event Trigger
    + Condition이 Event로 지정되며 Condition이 만족하면 특정 Animation과 같은 동작을 일으킴
    + EventTrigger RoutedEvent="name"
        + EventTrigger.Actions

Dependency Property
---
DP라고도 하며, 의존 프로퍼티라고 말하기도 한다. 기능적으로는 해당 값이 바뀌면 자동적으로 View에서 업데이트 해주는 것이다.

의존 프로퍼티는 항상 static readonly이다. 의존프로퍼티 값을 등록하는 방법은 아래와 같다

public static readonly DependencyProperty propertyname = DependencyPorperty.Register("propertyname", typeof(type), typeof(owner's class), new PropertyMetaData(초깃값))이다.