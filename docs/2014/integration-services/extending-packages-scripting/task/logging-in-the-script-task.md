---
title: Ведение журнала в задаче "Скрипт" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- SQL Server Integration Services packages, logs
- SSIS packages, logs
- logs [Integration Services], scripts
- Integration Services packages, logs
- Log method
- SSIS Script task, logs
- Script task [Integration Services], logs
- packages [Integration Services], logs
ms.assetid: 2e11fc15-df18-4309-bd2d-fc58aa4b9b7a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 425f0bc7cfd35e33c19aff6fda6eab0d3fc7b72e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48212616"
---
# <a name="logging-in-the-script-task"></a>Ведение журнала в задаче «Скрипт»
  Ведение журнала в пакетах служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] позволяет записывать для последующего анализа извлекаемую из стандартных событий или определяемых пользователем сообщений подробную информацию о ходе выполнения, полученных результатах и возникших проблемах. Задача «Скрипт» может использовать метод <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> объекта `Dts` для записи в журнал определяемых пользователем данных. Если ведение журнала разрешено и событие **ScriptTaskLogEntry** выбрано для записи в журнал на вкладке **Подробности** диалогового окна **Настройка журналов служб SSIS**, однократный вызов метода <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> сохраняет сведения о событиях во всех регистраторах, настроенных для данной задачи.  
  
> [!NOTE]  
>  Хотя журнал можно вести непосредственно из задачи «Скрипт», можно реализовать события вместо ведения журнала. При использовании событий можно не только включить запись в журнал сообщений о событиях, но и реагировать на события с помощью обработчиков событий, определяемых пользователем или заданных по умолчанию.  
  
 Дополнительные сведения о ведении журналов см. в разделе [Ведение журналов в службах Integration Services (SSIS)](../../performance/integration-services-ssis-logging.md).  
  
## <a name="logging-example"></a>Пример ведения журнала  
 Следующий пример иллюстрирует ведение журнала из задачи «Скрипт» путем записи в журнал значения, представляющего число обработанных строк.  
  
```vb  
Public Sub Main()  
  
    Dim rowsProcessed As Integer = 100  
    Dim emptyBytes(0) As Byte  
  
    Try  
        Dts.Log("Rows processed: " & rowsProcessed.ToString, _  
            0, _  
            emptyBytes)  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        'An error occurred.  
        Dts.Events.FireError(0, "Script Task Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class ScriptMain  
{  
  
    public void Main()  
        {  
            //  
            int rowsProcessed = 100;  
            byte[] emptyBytes = new byte[0];  
  
            try  
            {  
                Dts.Log("Rows processed: " + rowsProcessed.ToString(), 0, emptyBytes);  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                //An error occurred.  
                Dts.Events.FireError(0, "Script Task Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
        }  
```  
  
 }  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
-   Запись в блоге: [Ведение журнала пользовательских событий для задач служб Integration Services](http://go.microsoft.com/fwlink/?LinkId=165644), на сайте dougbert.com  
  
![Значок служб Integration Services (маленький)](../../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services** <br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Ведение журналов в службах Integration Services (SSIS)](../../performance/integration-services-ssis-logging.md)  
  
  
