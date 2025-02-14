﻿файлы URDF включают различные элементы XML, такие как <robot>, <link>,<joint>, вложенный в иерархических структурах, известных как деревья XML. Например,<link> и <joint> элементами, как говорят, являются дочерними элементами и, взаимно, <robot> - родительский элемент.

<robot>

`        `<link>

...

`        `</link>

`        `<link>

...

`        `</link>

`        `<joint>

...

`        `</joint>

</robot>

Дочерние элементы могут иметь свои дочерние элементы.

<link> элемент имеет дочерние элементы <inertial> и <visual>.

<visual> элемент имеет дочерние элементы <geometry> и <material>.

<material> элемент имеет дочерний элемент <color>.

<robot>

`        `<link>

`                `<inertial>

...

`                `</inertial>

`                `<visual>

`                        `<geometry>

...

`                        `</geometry>

`                        `<material>

`                                `<color />

`                        `</material>

`                `</visual>

`        `</link>

...

</robot>

В дополнение к дочерним элементам элементы XML в модели URDF могут иметь атрибуты. Например, <robot>, <link>, и <joint> элементы имеют атрибут <name>— строка, которая служит, чтобы идентифицировать элемент. <color> элемент имеет атрибут rgba— числовой массив с значением цвета.

Не все элементы и атрибуты, перечисленные в спецификации URDF, требуются. Некоторые, как <inertial> под <link>, являются дополнительными. Следующий код показывает различные элементы и атрибуты, что можно использовать с теми, которые являются дополнительным цветным зеленым.

\*Значения по умолчанию дополнительных атрибутов показывают в круглых скобках и в курсивном шрифте. Обратите внимание на то, что этот код включен только как ссылка и что он не представляет допустимую модель URDF. Многоточия (“...”) недопустимы в моделях URDF и используются просто, чтобы повредить длинные линии кода для простоты просмотра.



Геометрия <https://wiki.ros.org/urdf/XML/link#Attributes>

**Обязательные элементы :**

- <robot> - корневой элемент, который содержит всю модель робота. У него есть обязательный атрибут name, который служит для идентификации робота
- <link> - представляет собой отдельный компонент робота. У него есть обязательный атрибут name, который служит для идентификации ссылки
- <joint> - описывает связь между двумя ссылками. У него есть обязательные атрибуты name и type, которые служат для идентификации и определения типа соединения соответственно
- <parent> и <child> - внутри элемента <joint>, которые указывают на ссылки, между которыми установлено соединение
- <axis> - внутри элемента <joint>, который определяет ось вращения для вращательных соединений
- <limit> - внутри элемента <joint>, который определяет ограничения для движения соединения
- <origin> - внутри элементов <link>, <inertial>, <visual>, <collision>, и <joint>, который определяет положение и ориентацию этих элементов относительно родительского элемента

**дополнительные элементы:**

- <inertial> - описывает инерционные свойства ссылки. У него есть дочерние элементы <origin>, <mass>, и <inertia>. Элемент <origin> определяет положение и ориентацию инерциальной системы ссылок. Элемент <mass> определяет массу ссылки. Элемент <inertia> определяет инерцию ссылки
- <visual> - описывает визуальные свойства ссылки. У него есть дочерние элементы <origin>, <geometry>, и <material>. Элемент <origin> определяет положение и ориентацию визуальной системы ссылок. Элемент <geometry> определяет геометрию ссылки. Элемент <material> определяет материал ссылки
- <collision> - описывает свойства столкновения ссылки. У него есть дочерние элементы <origin>, и <geometry>. Элемент <origin> определяет положение и ориентацию системы столкновения ссылок. Элемент <geometry> определяет геометрию столкновения ссылки
- <geometry> - описывает геометрию ссылки. У него есть дочерние элементы <box>, <cylinder>, <sphere>, и <mesh>. Элементы определяет геометрию ссылки в виде прямоугольного параллелепипеда, цилиндра, сферы, сетки соответственно.
- <material> - описывает материал ссылки. У него есть дочерний элемент <color>, который определяет цвет ссылки
- <dynamics> - описывает динамические свойства ссылки. У него есть дочерние элементы <damping> и <friction>, которые определяют затухание и трение ссылки соответственно
- <limit> - описывает ограничения для движения соединения. У него есть дочерние элементы <lower>, <upper>, <effort>, и <velocity>, которые определяют нижний, верхний пределы, усилие, и скорость движения соединения соответственно
- <mimic> - описывает соединения, которые следуют за другими соединениями. У него есть дочерние элементы <joint>, <multiplier>, и <offset>, которые определяют соединение, множитель, и смещение соответственно
- <safety\_controller> - описывает безопасный контроллер для соединения. У него есть дочерние элементы <soft\_lower\_limit>, <soft\_upper\_limit>, <k\_position>, и <k\_velocity>, которые определяют мягкий нижний предел, мягкий верхний предел, коэффициент позиции, и коэффициент скорости соответственно

\*для работы с urdf можно использовать urdf editor online, но не знаю, насколько это удобно
