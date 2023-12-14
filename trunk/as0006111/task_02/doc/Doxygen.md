# Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`Controller`](#class_controller) | Класс регулятора
`class `[`Linear`](#class_linear) | Класс, который служит для реализации линейной модели
`class `[`Model`](#class_model) | Класс, который необходим классам, рассчитывающим линейную и нелинейную модель.
`class `[`Non_Linear`](#class_non___linear) | Класс, который служит для реализации нелинейной модели

# class `Controller` 

Класс регулятора

Отдельный класс, в котором мы моделируем регулятор

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public inline  `[`Controller`](#class_controller_1a2febb6d65c48c4af1b4a13b4d9b5e355)`(double K,double T0,double TD,double T)` | 
`public inline double `[`Heat`](#class_controller_1a01da93f3d69e933aa60afc9e264e294e)`(double e,double e0,double e1)` | 

## Members

#### `public inline  `[`Controller`](#class_controller_1a2febb6d65c48c4af1b4a13b4d9b5e355)`(double K,double T0,double TD,double T)` 

#### `public inline double `[`Heat`](#class_controller_1a01da93f3d69e933aa60afc9e264e294e)`(double e,double e0,double e1)` 

# class `Linear` 

```
class Linear
  : public Model
```  

Класс, который служит для реализации линейной модели

Дочерний класс от [Model](#class_model), который реализует линейную модель через функцию expression

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public inline  `[`Linear`](#class_linear_1af613466cfc09060d0a6460457d964103)`(double a,double b)` | 
`public inline virtual double `[`expression`](#class_linear_1a5810d335fab1135e1fe716605ee6d842)`(double heat,double y)` | Метод для рассчёта линейной модели
`public  `[`~Linear`](#class_linear_1a49ed05abff48d7ded39b10fa4ecdc5ab)`() = default` | 

## Members

#### `public inline  `[`Linear`](#class_linear_1af613466cfc09060d0a6460457d964103)`(double a,double b)` 

#### `public inline virtual double `[`expression`](#class_linear_1a5810d335fab1135e1fe716605ee6d842)`(double heat,double y)` 

Метод для рассчёта линейной модели

Код: 
```cpp
 y = a * y + b * heat;
return y;
```

#### `public  `[`~Linear`](#class_linear_1a49ed05abff48d7ded39b10fa4ecdc5ab)`() = default` 

# class `Model` 

Класс, который необходим классам, рассчитывающим линейную и нелинейную модель.

Класс, который предоставляет виртуальную функцию уравнения expression и от которого наследуются классы [Linear](#class_linear) и [Non_Linear](#class_non___linear)

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public double `[`expression`](#class_model_1af65899fb2e7fc2ae0767ae7d38133b4e)`(double heat,double y)` | 
`public virtual  `[`~Model`](#class_model_1a2efbe4ec768191fa70ad86f260ec2fd6)`() = default` | 

## Members

#### `public double `[`expression`](#class_model_1af65899fb2e7fc2ae0767ae7d38133b4e)`(double heat,double y)` 

#### `public virtual  `[`~Model`](#class_model_1a2efbe4ec768191fa70ad86f260ec2fd6)`() = default` 

# class `Non_Linear` 

```
class Non_Linear
  : public Model
```  

Класс, который служит для реализации нелинейной модели

Дочерний класс от [Model](#class_model), который реализует нелинейную модель через функцию expression

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public inline  `[`Non_Linear`](#class_non___linear_1a7d2ae20f0c648a0a421f16733d07885a)`(double a,double b,double c,double d)` | 
`public inline virtual double `[`expression`](#class_non___linear_1a5fc7e3c9f6d6b51aef6c0895b33784db)`(double heat,double y)` | Метод для рассчёта нелинейной модели
`public  `[`~Non_Linear`](#class_non___linear_1a0634334e5772e6a651ecfef97040be56)`() = default` | 

## Members

#### `public inline  `[`Non_Linear`](#class_non___linear_1a7d2ae20f0c648a0a421f16733d07885a)`(double a,double b,double c,double d)` 

#### `public inline virtual double `[`expression`](#class_non___linear_1a5fc7e3c9f6d6b51aef6c0895b33784db)`(double heat,double y)` 

Метод для рассчёта нелинейной модели

Код: 
```cpp
auto y1 = a * y - b * pow(y0, 2) + c * heat + d * sin(heat0);
y0 = y;
heat0 = heat;
return y1;
```

#### `public  `[`~Non_Linear`](#class_non___linear_1a0634334e5772e6a651ecfef97040be56)`() = default` 

Generated by [Moxygen](https://sourcey.com/moxygen)