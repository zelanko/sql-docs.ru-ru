---
title: Имитация вывода ошибок для компонента скрипта | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], error output
- error outputs [Integration Services], Script component
ms.assetid: f8b6ecff-ac99-4231-a0e7-7ce4ad76bad0
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 17f6ed6fd86bb7440f795268e63aa7b9ba418afb
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968548"
---
# <a name="simulating-an-error-output-for-the-script-component"></a>Имитация вывода ошибок для компонента скрипта
  Хотя невозможно напрямую настроить вывод ошибок в компоненте скрипта для автоматической обработки строк ошибок, можно воспроизвести функциональность встроенного вывода ошибок, создав дополнительный выход и используя условную логику в скрипте для направления строк на этот выход, когда это целесообразно. Возможно, потребуется имитация поведения встроенного вывода ошибок с помощью добавления двух дополнительных выходных столбцов для номера ошибки и идентификатора столбца, в котором эта ошибка возникла.  
  
 Если необходимо добавить описание ошибки, соответствующее конкретному стандартному коду ошибки служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], можно использовать метод <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> интерфейса <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>, доступ к которому можно получить через свойство <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> компонента скрипта.  
  
## <a name="example"></a>Пример  
 В следующем примере используется компонент скрипта, настроенный в качестве преобразования и имеющий два синхронных выхода. Этот компонент скрипта предназначен для фильтрации строк ошибок в строках, содержащих адреса, в образце базы данных AdventureWorks. Вымышленная ситуация, рассматриваемая в этом примере, предполагает увеличение количества клиентов в Северной Америке, в результате чего возникает необходимость выполнить фильтрацию, исключающую адреса, расположенные за пределами Северной Америки.  
  
#### <a name="to-configure-the-example"></a>Настройка примера  
  
1.  Перед созданием нового компонента скрипта создайте диспетчер соединений и настройте источник потока данных, выбирающий адреса из образца базы данных AdventureWorks. В этом примере, где предусмотрено обращение только к столбцу CountryRegionName, можно просто использовать представление Person.vStateCountryProvinceRegion либо выбрать данные, соединив таблицы Person.Address, Person.StateProvince и Person.CountryRegion.  
  
2.  Добавьте новый компонент скрипта в область конструктора потока данных и настройте его в качестве преобразования. Откройте **редактор преобразования "Скрипт"** .  
  
3.  На странице **Скрипт** задайте свойство **ScriptLanguage**, указав язык скрипта, используемый для создания скрипта.  
  
4.  Нажмите кнопку **Изменить скрипт**, чтобы открыть среду [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).  
  
5.  В методе `Input0_ProcessInputRow` введите или вставьте следующий образец кода:  
  
6.  Закройте среду VSTA.  
  
7.  На странице **Входные столбцы** выберите столбцы, которые необходимо обработать в преобразовании "Скрипт". В этом примере используется только столбец CountryRegionName. Невыбранные доступные входные столбцы будут пропущены без изменения в потоке данных.  
  
8.  На странице **входы и выходы** добавьте новый, второй выход и задайте `SynchronousInputID` для его значения идентификатор входа, который также является значением `SynchronousInputID` свойства выходного значения по умолчанию. Присвойте свойству `ExclusionGroup` обоих выходов одно и то же ненулевое значение (например, 1), чтобы указать, что каждая строка должна быть направлена только в один из двух выходов. Дайте новому выводу ошибок понятное описательное имя, например MyErrorOutput.  
  
9. Добавьте в новый вывод ошибок дополнительные выходные столбцы для отслеживания требуемых данных ошибок. В их число может входить код ошибки, идентификатор столбца, в котором возникла ошибка, а также, возможно, описание ошибки. В этом примере создаются новые столбцы, ErrorColumn и ErrorMessage. Если в реализации обрабатываются стандартные ошибки служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], необходимо добавить столбец ErrorCode для номера ошибки.  
  
10. Запишите значение идентификатора входного столбца или столбцов, которые должны проверяться компонентом скрипта на наличие ошибок. В этом примере идентификатор столбца используется для заполнения значений в столбце ErrorColumn.  
  
11. Закройте **редактор преобразования "Скрипт"** .  
  
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
  
![Значок Integration Services (маленький)](../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также:  
 [Обработка ошибок в данных](../data-flow/error-handling-in-data.md)   
 [Использование вывода ошибок в компоненте потока данных](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)   
 [Создание синхронного преобразования с помощью компонента скрипта](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) 
  
  
