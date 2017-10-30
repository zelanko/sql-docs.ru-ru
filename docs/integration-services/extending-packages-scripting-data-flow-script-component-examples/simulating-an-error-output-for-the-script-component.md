---
title: "Имитация вывода ошибок для компонента скрипта | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], error output
- error outputs [Integration Services], Script component
ms.assetid: f8b6ecff-ac99-4231-a0e7-7ce4ad76bad0
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 0af8434531660958557928376cf8a4fd19ca9e68
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="simulating-an-error-output-for-the-script-component"></a>Имитация вывода ошибок для компонента скрипта
  Хотя невозможно напрямую настроить вывод ошибок в компоненте скрипта для автоматической обработки строк ошибок, можно воспроизвести функциональность встроенного вывода ошибок, создав дополнительный выход и используя условную логику в скрипте для направления строк на этот выход, когда это целесообразно. Возможно, потребуется имитация поведения встроенного вывода ошибок с помощью добавления двух дополнительных выходных столбцов для номера ошибки и идентификатора столбца, в котором эта ошибка возникла.  
  
 Если необходимо добавить описание ошибки, соответствующее конкретному стандартному коду ошибки служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], можно использовать метод <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> интерфейса <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>, доступ к которому можно получить через свойство <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> компонента скрипта.  
  
## <a name="example"></a>Пример  
 В следующем примере используется компонент скрипта, настроенный в качестве преобразования и имеющий два синхронных выхода. Этот компонент скрипта предназначен для фильтрации строк ошибок в строках, содержащих адреса, в образце базы данных AdventureWorks. Вымышленная ситуация, рассматриваемая в этом примере, предполагает увеличение количества клиентов в Северной Америке, в результате чего возникает необходимость выполнить фильтрацию, исключающую адреса, расположенные за пределами Северной Америки.  
  
#### <a name="to-configure-the-example"></a>Настройка примера  
  
1.  Перед созданием нового компонента скрипта создайте диспетчер соединений и настройте источник потока данных, выбирающий адреса из образца базы данных AdventureWorks. В этом примере, где предусмотрено обращение только к столбцу CountryRegionName, можно просто использовать представление Person.vStateCountryProvinceRegion либо выбрать данные, соединив таблицы Person.Address, Person.StateProvince и Person.CountryRegion.  
  
2.  Добавьте новый компонент скрипта в область конструктора потока данных и настройте его в качестве преобразования. Откройте **редактор преобразования «скрипт»**.  
  
3.  На **сценарий** задайте **ScriptLanguage** свойства язык сценария, который будет использоваться для создания скрипта.  
  
4.  Нажмите кнопку **Изменить скрипт** , чтобы открыть среду [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).  
  
5.  В **Input0_ProcessInputRow** метод, введите или вставьте следующий образец кода.  
  
6.  Закройте среду VSTA.  
  
7.  На **входные столбцы** выберите столбцы, которые необходимо обработать в преобразовании «скрипт». В этом примере используется только столбец CountryRegionName. Невыбранные доступные входные столбцы будут пропущены без изменения в потоке данных.  
  
8.  На **входы и выходы** страницы, добавьте новый, второй выход и задать его **SynchronousInputID** значение идентификатора входа, которое также является значением из **SynchronousInputID** свойство выхода по умолчанию. Задать **ExclusionGroup** свойства обоих выходов же ненулевое значение (например, 1), чтобы указать, что каждая строка направляется только к одной из двух выходов. Дайте новому выводу ошибок понятное описательное имя, например MyErrorOutput.  
  
9. Добавьте в новый вывод ошибок дополнительные выходные столбцы для отслеживания требуемых данных ошибок. В их число может входить код ошибки, идентификатор столбца, в котором возникла ошибка, а также, возможно, описание ошибки. В этом примере создаются новые столбцы, ErrorColumn и ErrorMessage. Если в реализации обрабатываются стандартные ошибки служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], необходимо добавить столбец ErrorCode для номера ошибки.  
  
10. Запишите значение идентификатора входного столбца или столбцов, которые должны проверяться компонентом скрипта на наличие ошибок. В этом примере идентификатор столбца используется для заполнения значений в столбце ErrorColumn.  
  
11. Закрыть **редактор преобразования «скрипт».**  
  
12. Соедините выходы компонента скрипта с подходящими назначениями. Назначение «Неструктурированный файл» проще всего для настройки тестирования в нерегламентированных случаях.  
  
13. Запустите пакет.  
  
```vb  
Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
  If Row.CountryRegionName <> "Canada" _  
      And Row.CountryRegionName <> "United States" Then  
  
    Row.ErrorColumn = 68 ' ID of CountryRegionName column  
    Row.ErrorMessage = "Address is not in North America."  
    Row.DirectRowToMyErrorOutput()  
  
  Else  
  
    Row.DirectRowToOutput0()  
  
  End If  
  
End Sub  
```  
  
```csharp  
public override void Input0_ProcessInputRow(Input0Buffer Row)  
{  
  
  if (Row.CountryRegionName!="Canada"&&Row.CountryRegionName!="United States")  
  
  {  
    Row.ErrorColumn = 68; // ID of CountryRegionName column  
    Row.ErrorMessage = "Address is not in North America.";  
    Row.DirectRowToMyErrorOutput();  
  
  }  
  else  
  {  
  
    Row.DirectRowToOutput0();  
  
  }  
  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Обработка ошибок в данных](../../integration-services/data-flow/error-handling-in-data.md)   
 [Использование выводов ошибок в компоненте потока данных](../../integration-services/extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)   
 [Создание синхронного преобразования с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)  
  
  

