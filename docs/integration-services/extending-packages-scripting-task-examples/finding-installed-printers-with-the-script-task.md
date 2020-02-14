---
title: Обнаружение установленных принтеров с помощью задачи "Скрипт" | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- System.Drawing.Printing namespace
- printers [Integration Services]
- SSIS Script task, printers
- locating printers
- Printing namespace
- Script task [Integration Services], examples
- finding printers [SQL Server]
- Script task [Integration Services], printers
ms.assetid: 50a55014-e2c3-4ecd-84e1-3e877c55a260
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cece5cb3e406bdc0fe5b437691528eb4cf6bf848
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71286857"
---
# <a name="finding-installed-printers-with-the-script-task"></a>Обнаружение установленных принтеров с помощью задачи «Скрипт»

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Данные, преобразуемые с помощью пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], часто имеют в качестве своего конечного назначения печатаемый отчет. Пространство имен **System.Drawing.Printing** на платформе [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] предоставляет классы для работы с принтерами.  
  
> [!NOTE]  
>  Если нужно создать задачу, которую будет удобно использовать в нескольких пакетах, рекомендуется начать разработку пользовательской задачи с этого образца задачи «Скрипт». Дополнительные сведения см. в разделе [Разработка пользовательской задачи](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a>Описание  
 В следующем примере показано, как выполняется поиск установленных на сервере принтеров, которые поддерживают формат бумаги «стандарт» (применяемую в Соединенных Штатах). Код проверки поддерживаемых форматов бумаги инкапсулирован в закрытой функции. Чтобы можно было следить за ходом выполнения в скрипте проверок параметров для каждого принтера, в скрипте используется метод <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> для инициирования информационного сообщения для принтеров, поддерживающих формат бумаги «стандарт», и инициирования предупреждения для принтеров, не поддерживающих формат бумаги «стандарт». Эти сообщения появляются в окне **Вывод** интегрированной среды разработки средств [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для приложений (VSTA) при выполнении пакета в конструкторе.  
  
#### <a name="to-configure-this-script-task-example"></a>Настройка этого образца задачи «Скрипт»  
  
1.  Создайте переменную с именем `PrinterList` типа **Object**.  
  
2.  На странице **Скрипт** в **редакторе задачи "Скрипт"** добавьте эту переменную к свойству ReadWriteVariables.  
  
3.  В проекте скрипта добавьте ссылку на пространство имен **System.Drawing**.  
  
4.  В коде используйте инструкции **Imports** для импорта пространств имен **System.Collections** и **System.Drawing.Printing**.  
  
### <a name="code"></a>Код  
  
```vb  
Public Sub Main()  
  
    Dim printerName As String  
    Dim currentPrinter As New PrinterSettings  
    Dim size As PaperSize  
  
    Dim printerList As New ArrayList  
    For Each printerName In PrinterSettings.InstalledPrinters  
        currentPrinter.PrinterName = printerName  
        If PrinterHasLegalPaper(currentPrinter) Then  
            printerList.Add(printerName)  
            Dts.Events.FireInformation(0, "Example", _  
                "Printer " & printerName & " has legal paper.", _  
                String.Empty, 0, False)  
        Else  
            Dts.Events.FireWarning(0, "Example", _  
                "Printer " & printerName & " DOES NOT have legal paper.", _  
                String.Empty, 0)  
        End If  
    Next  
  
    Dts.Variables("PrinterList").Value = printerList  
  
    Dts.TaskResult = ScriptResults.Success  
  
End Sub  
  
Private Function PrinterHasLegalPaper( _  
    ByVal thisPrinter As PrinterSettings) As Boolean  
  
    Dim size As PaperSize  
    Dim hasLegal As Boolean = False  
  
    For Each size In thisPrinter.PaperSizes  
        If size.Kind = PaperKind.Legal Then  
            hasLegal = True  
        End If  
    Next  
  
    Return hasLegal  
  
End Function  
```  
  
```csharp  
public void Main()  
        {  
  
            PrinterSettings currentPrinter = new PrinterSettings();  
            PaperSize size;  
            Boolean Flag = false;  
  
            ArrayList printerList = new ArrayList();  
            foreach (string printerName in PrinterSettings.InstalledPrinters)  
            {  
                currentPrinter.PrinterName = printerName;  
                if (PrinterHasLegalPaper(currentPrinter))  
                {  
                    printerList.Add(printerName);  
                    Dts.Events.FireInformation(0, "Example", "Printer " + printerName + " has legal paper.", String.Empty, 0, ref Flag);  
                }  
                else  
                {  
                    Dts.Events.FireWarning(0, "Example", "Printer " + printerName + " DOES NOT have legal paper.", String.Empty, 0);  
                }  
            }  
  
            Dts.Variables["PrinterList"].Value = printerList;  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
        private bool PrinterHasLegalPaper(PrinterSettings thisPrinter)  
        {  
  
            bool hasLegal = false;  
  
            foreach (PaperSize size in thisPrinter.PaperSizes)  
            {  
                if (size.Kind == PaperKind.Legal)  
                {  
                    hasLegal = true;  
                }  
            }  
  
            return hasLegal;  
  
        }  
```  
  
## <a name="see-also"></a>См. также:  
 [Примеры задачи «Скрипт»](../../integration-services/extending-packages-scripting-task-examples/script-task-examples.md)  
  
  
