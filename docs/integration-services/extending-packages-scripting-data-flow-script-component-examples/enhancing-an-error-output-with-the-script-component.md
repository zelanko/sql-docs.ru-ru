---
title: "Расширение вывода ошибок с помощью компонента скрипта | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting-data-flow-script-component-examples
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- transformations [Integration Services], components
- Script component [Integration Services], examples
- error outputs [Integration Services], enhancing
- Script component [Integration Services], transformation components
ms.assetid: f7c02709-f1fa-4ebd-b255-dc8b81feeaa5
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 3881b57f4089dbb075d019f9bd1a88a96a307b72
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="enhancing-an-error-output-with-the-script-component"></a>Расширение вывода ошибок с помощью компонента скрипта
  По умолчанию два дополнительных столбца в [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] вывод ошибок, ErrorCode и ErrorColumn, содержат только числовые коды, представляющие номер ошибки и идентификатор столбца, в котором произошла ошибка. Эти числовые значения могут быть малополезны без соответствующего описания ошибки и имя столбца.  
  
 В этом разделе описывается добавление описания ошибки и имя столбца к существующим выходным данным ошибок в потоке данных с помощью компонента скрипта. В следующем примере с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> интерфейса <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>, доступ к которому можно получить через свойство <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> компонента скрипта, добавляется описание ошибки, соответствующее конкретному стандартному коду ошибки служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Затем в примере добавляется имя столбца, который соответствует идентификатору записанного журнала обращений и преобразований с помощью <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData130.GetIdentificationStringByID%2A> метод одного интерфейса.  
  
> [!NOTE]  
>  Если нужно создать компонент, который будет полезен в нескольких задачах потока данных и нескольких пакетах, рекомендуется в качестве основы использовать этот образец компонента скрипта. Дополнительные сведения см. в разделе [Разработка пользовательского компонента потока данных](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="example"></a>Пример  
 В следующем примере использует компонент скрипта, настроенный в качестве преобразования для добавления описание ошибки и имя столбца к существующим выходным данным ошибок в потоке данных.  
  
 Дополнительные сведения о том, как настроить компонент скрипта для использования в качестве преобразования в потоке данных см. в разделе [создание синхронного преобразования с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) и [Создание асинхронного преобразования с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).  
  
#### <a name="to-configure-this-script-component-example"></a>Настройка этого примера компонента скрипта  
  
1.  Перед созданием нового компонента скрипта настройте вышестоящий компонент в потоке данных для перенаправления строк в его вывод ошибок при возникновении ошибки или усечения. В целях тестирования, возможно, следует настроить компонент таким образом, чтобы гарантировать возникновение ошибок, — например, настроив преобразование «Уточняющий запрос» между двумя таблицами, в котором уточняющий запрос непременно приведет к ошибке.  
  
2.  Добавьте новый компонент скрипта в область конструктора потока данных и настройте его в качестве преобразования.  
  
3.  Соедините вывод ошибок вышестоящего компонента с новым компонентом скрипта.  
  
4.  Откройте **редактор преобразования «скрипт»**и на **сценарий** страницы, для **ScriptLanguage** свойства, выберите язык сценария.  
  
5.  Нажмите кнопку **изменить скрипт** Открытие [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] средств для приложений (VSTA) интегрированной среды разработки и добавьте следующий образец кода.  
  
6.  Закройте среду VSTA.  
  
7.  В редакторе сценариев преобразования на **входные столбцы** выберите столбцы ErrorCode и ErrorColumn.  
  
8.  На **входы и выходы** добавьте два новых столбца.  
  
    -   Добавьте новый выходной столбец типа **строка** с именем **ErrorDescription**. Увеличьте длину нового столбца по умолчанию до 255 для поддержки длинных сообщений.  
  
    -   Добавьте другой новый выходной столбец типа **строка** с именем **ColumnName**. Увеличьте длину нового столбца до 255 для поддержки длинные значения по умолчанию.  
  
9. Закрыть **редактор преобразования «скрипт».**  
  
10. Соедините выход компонента скрипта с подходящим назначением. Назначение «Неструктурированный файл» проще всего при настройке в случае нерегламентированной отладки.  
  
11. Запустите пакет.  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
      Row.ErrorDescription = _  
        Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
  
      Dim componentMetaData130 = TryCast(Me.ComponentMetaData, IDTSComponentMetaData130)  
      If componentMetaData130 IsNot Nothing Then  
        Row.ColumnName = componentMetaData130.GetIdentificationStringByID(Row.ErrorColumn)  
         End If  
  
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
  
      var componentMetaData130 = this.ComponentMetaData as IDTSComponentMetaData130;  
      if (componentMetaData130 != null)  
        {  
            Row.ColumnName = componentMetaData130.GetIdentificationStringByID(Row.ErrorColumn);  
        }  
  
    }  
}  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Обработка ошибок в данных](../../integration-services/data-flow/error-handling-in-data.md)   
 [Использование выводов ошибок в компоненте потока данных](../../integration-services/extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)   
 [Создание синхронного преобразования с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)   
  
  

