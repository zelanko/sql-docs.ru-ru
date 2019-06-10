---
title: Расширение вывода ошибок с помощью компонента скрипта | Документы Майкрософт
ms.custom: ''
ms.date: 01/04/2019
ms.prod: sql
ms.prod_service: integration-services
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
ms.openlocfilehash: 3c9a7827c70f99db24c50704f2591b8288124d45
ms.sourcegitcommit: cb86e7b75c2b40c2c5ff2a6c1be0e6bd17b03f9a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/03/2019
ms.locfileid: "66469677"
---
# <a name="enhancing-an-error-output-with-the-script-component"></a>Расширение вывода ошибок с помощью компонента скрипта

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  По умолчанию два дополнительных столбца в выводе ошибок служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], ErrorCode и ErrorColumn, содержат только числовые коды, представляющие номер ошибки и идентификатор столбца, в котором произошла ошибка. Эти числовые значения могут быть малополезны без соответствующего описания ошибки и имени столбца.  
  
 В этом разделе описывается, как добавить имя столбца и описание ошибки к существующим выходным данным ошибок в потоке данных с помощью компонента скрипта. В следующем примере с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> интерфейса <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>, доступ к которому можно получить через свойство <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> компонента скрипта, добавляется описание ошибки, соответствующее конкретному стандартному коду ошибки служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Затем в примере с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData130.GetIdentificationStringByID%2A> того же интерфейса добавляется имя столбца, соответствующее зарегистрированному идентификатору журнала обращений и преобразований.  
  
> [!NOTE]  
>  Если нужно создать компонент, который будет полезен в нескольких задачах потока данных и нескольких пакетах, рекомендуется в качестве основы использовать этот образец компонента скрипта. Дополнительные сведения см. в разделе [Разработка пользовательского компонента потока данных](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="example"></a>Пример  
 В приведенном примере компонент скрипта, настроенный в качестве преобразования, используется для добавления имени столбца и описания ошибки к существующим выходным данным ошибок в потоке данных.  
  
 Дополнительные сведения о том, как настроить компонент скрипта для использования в качестве преобразования в потоке данных см. в разделах [Создание синхронного преобразования с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) и [Создание асинхронного преобразования с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).  
  
#### <a name="to-configure-this-script-component-example"></a>Настройка этого примера компонента скрипта  
  
1.  Перед созданием нового компонента скрипта настройте вышестоящий компонент в потоке данных для перенаправления строк в его вывод ошибок при возникновении ошибки или усечения. В целях тестирования, возможно, следует настроить компонент таким образом, чтобы гарантировать возникновение ошибок, — например, настроив преобразование "Уточняющий запрос" между двумя таблицами, в котором уточняющий запрос непременно приведет к ошибке.  
  
2.  Добавьте новый компонент скрипта в область конструктора потока данных и настройте его в качестве преобразования.  
  
3.  Соедините вывод ошибок вышестоящего компонента с новым компонентом скрипта.  
  
4.  Откройте **Редактор преобразования "Скрипт"** и на странице **Скрипт** для свойства **ScriptLanguage** выберите язык скрипта.  
  
5.  Нажмите кнопку **Изменить скрипт**, чтобы открыть интегрированную среду разработки средств [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для приложений (VSTA), и добавьте приведенный ниже пример кода.  
  
6.  Закройте среду VSTA.  
  
7.  В редакторе преобразования "Скрипт" на странице **Входные столбцы** выберите столбцы ErrorCode и ErrorColumn.  
  
8.  На странице **Входы и выходы** добавьте два новых столбца.  
  
    -   Добавьте новый выходной столбец типа **String** с именем **ErrorDescription**. Увеличьте длину нового столбца по умолчанию до 255 для поддержки длинных сообщений.  
  
    -   Добавьте еще один новый выходной столбец типа **String** с именем **ColumnName**. Увеличьте длину нового столбца по умолчанию до 255 для поддержки длинных значений.  
  
9. Закройте **редактор преобразования "Скрипт"** .  
  
10. Соедините выход компонента скрипта с подходящим назначением. Назначение «Неструктурированный файл» проще всего при настройке в случае нерегламентированной отладки.  
  
11. Запустите пакет.  

```vb
Public Class ScriptMain      ' VB
    Inherits UserComponent
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)

        Row.ErrorDescription = _
            Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)

        Dim componentMetaData130 = TryCast(Me.ComponentMetaData, IDTSComponentMetaData130)

        If componentMetaData130 IsNot Nothing Then

            If Row.ErrorColumn = 0 Then
                ' 0 means no specific column is identified by ErrorColumn, this time.
                Row.ColumnName = "Check the row for a violation of a foreign key constraint."
            ELSE If Row.ErrorColumn = -1 Then
                ' -1 means you are using Table Lock for a Memory Optimised destination table which is not supported.
                Row.ColumnName = "Table lock is not compatible with Memory Optimised tables."
            Else
                Row.ColumnName = componentMetaData130.GetIdentificationStringByID(Row.ErrorColumn)
            End If
        End If
    End Sub
End Class
```

```csharp
public class ScriptMain:      // C#
    UserComponent
{
    public override void Input0_ProcessInputRow(Input0Buffer Row)
    {
        Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);

        var componentMetaData130 = this.ComponentMetaData as IDTSComponentMetaData130;
        if (componentMetaData130 != null)
        {
            // 0 means no specific column is identified by ErrorColumn, this time.
            if (Row.ErrorColumn == 0)
            {
                Row.ColumnName = "Check the row for a violation of a foreign key constraint.";
            }
            // -1 means you are using Table Lock for a Memory Optimised destination table which is not supported.
            else if (Row.ErrorColumn == -1)
            {
                Row.ColumnName = "Table lock is not compatible with Memory Optimised tables.";
            }
            else
            {
                Row.ColumnName = componentMetaData130.GetIdentificationStringByID(Row.ErrorColumn);
            }
        }
    }
}
```

## <a name="see-also"></a>См. также:  
 [Обработка ошибок в данных](../../integration-services/data-flow/error-handling-in-data.md)   
 [Использование выводов ошибок в компоненте потока данных](../../integration-services/extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)   
 [Создание синхронного преобразования с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)   
  
  
