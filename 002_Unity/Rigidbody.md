***Fixed update() происходит перед расчетом физики в Unity***
##### Interpolate
- ***Interpolate*** - Расчитывает среднее значение для плавного рендерига движущегося обьекта на основе предыдущего кадра
- ***Extrapolate*** - на приблизительной трансформации следующего кадра

##### [[Static, Kinematic, Dynamic]]
##### Collision detection
- ***Discrete*** - никак не расчитывает предварительно обнаружение колизии (для статических или медленно движущихся обьектов)
- ***Continuous*** - для быстрых обьектов, которые взаимодействуют с дискретными
- ***Continuous dynamic*** - для быстрого обьекта, который взаимодействует с *continuous* обьектом

##### Force mode
|   |   |
|---|---|
|[Force](https://docs.unity3d.com/ru/530/ScriptReference/ForceMode.Force.html)|Добавить физическому телу постоянную силу, учитывая его массу.|
|[Acceleration](https://docs.unity3d.com/ru/530/ScriptReference/ForceMode.Acceleration.html)|Добавить физическому телу постоянное ускорение, игнорируя его массу.|
|[Impulse](https://docs.unity3d.com/ru/530/ScriptReference/ForceMode.Impulse.html)|Добавить физическому телу мгновенный импульс силы, учитывая его массу.|
|[VelocityChange](https://docs.unity3d.com/ru/530/ScriptReference/ForceMode.VelocityChange.html)|Добавить физическому телу мгновенное изменение скорости, игнорируя его массу.|
