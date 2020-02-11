---
title: Расширение вывода ошибок с помощью компонента скрипта | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- transformations [Integration Services], components
- Script component [Integration Services], examples
- error outputs [Integration Services], enhancing
- Script component [Integration Services], transformation components
ms.assetid: f7c02709-f1fa-4ebd-b255-dc8b81feeaa5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3dd935387e8d6e4a95a25d21eb5d5d229f9599bd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62895493"
---
# <a name="enhancing-an-error-output-with-the-script-component"></a>Расширение вывода ошибок с помощью компонента скрипта
  По умолчанию два дополнительных столбца в выводе ошибок служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], ErrorCode и ErrorColumn, содержат только числовые коды, представляющие номер ошибки и идентификатор столбца, в котором произошла ошибка. Эти числовые значения могут быть малополезны без соответствующего описания ошибки.  
  
 В этом разделе описывается, как добавить столбец с описанием ошибки к существующим выходным данным ошибок в потоке данных с помощью компонента скрипта. В следующем примере с помощью метода [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] интерфейса <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A>, доступ к которому можно получить через свойство <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> компонента скрипта, добавляется описание ошибки, соответствующее конкретному стандартному коду ошибки служб <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A>.  
  
> [!NOTE]  
>  Если нужно создать компонент, который будет полезен в нескольких задачах потока данных и нескольких пакетах, рекомендуется в качестве основы использовать этот образец компонента скрипта. Дополнительные сведения см. в разделе [Разработка пользовательского компонента потока данных](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="example"></a>Пример  
 В приведенном примере компонент скрипта, настроенный в качестве преобразования, используется для добавления столбца с описанием ошибки к существующим выходным данным ошибок в потоке данных.  
  
 Дополнительные сведения о настройке компонента скрипта для использования в качестве преобразования в потоке данных см. в разделе [Создание синхронного преобразования с помощью компонента скрипта](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)и [Создание асинхронного преобразования с помощью компонента скрипта](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).  
  
#### <a name="to-configure-this-script-component-example"></a>Настройка этого примера компонента скрипта  
  
1.  Перед созданием нового компонента скрипта настройте вышестоящий компонент в потоке данных для перенаправления строк в его вывод ошибок при возникновении ошибки или усечения. В целях тестирования, возможно, следует настроить компонент таким образом, чтобы гарантировать возникновение ошибок, — например, настроив преобразование "Уточняющий запрос" между двумя таблицами, в котором уточняющий запрос непременно приведет к ошибке.  
  
2.  Добавьте новый компонент скрипта в область конструктора потока данных и настройте его в качестве преобразования.  
  
3.  Соедините вывод ошибок вышестоящего компонента с новым компонентом скрипта.  
  
4.  Откройте **Редактор преобразования "Скрипт"** и на странице **Скрипт** для свойства **ScriptLanguage** выберите язык скрипта.  
  
5.  Нажмите кнопку **Изменить скрипт**, чтобы открыть интегрированную среду разработки средств [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для приложений (VSTA), и добавьте приведенный ниже пример кода.  
  
6.  Закройте среду VSTA.  
  
7.  В редакторе преобразования «Скрипт» на странице « **входные столбцы** » выберите столбец ErrorCode.  
  
8.  На странице **входы и выходы** добавьте новый выходной столбец типа `String` с именем **ErrorDescription**. Увеличьте длину нового столбца по умолчанию до 255 для поддержки длинных сообщений.  
  
9. Закройте **редактор преобразования "Скрипт"**.  
  
10. Соедините выход компонента скрипта с подходящим назначением. Назначение «Неструктурированный файл» проще всего при настройке в случае нерегламентированной отладки.  
  
11. Запустите пакет.  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
  Row.ErrorDescription = _  
    Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
  
    End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain:  
    UserComponent  
{  
    public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
  Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
  
    }  
}  
  
```  
  
![Значок Integration Services (маленький)](../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также:  
 [Обработка ошибок в данных](../data-flow/error-handling-in-data.md)   
 [Использование вывода ошибок в компоненте потока данных](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)   
 [Создание синхронного преобразования с помощью компонента скрипта](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) 
  
  
