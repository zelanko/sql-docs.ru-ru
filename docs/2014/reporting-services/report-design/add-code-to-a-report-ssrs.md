---
title: Добавление кода в отчет (службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- code [Reporting Services]
- custom code [Reporting Services]
- expressions [Reporting Services], code
- adding code
- reports [Reporting Services], code
ms.assetid: 00ef8fc6-99fe-49b2-8a22-7eb475881dc4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e8109678c3e9695b842eb57b976da9e653afd737
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66106660"
---
# <a name="add-code-to-a-report-ssrs"></a>Добавление кода в отчет (службы SSRS)
  В любом выражении можно вызвать собственный пользовательский код. Данный код можно предоставить следующими способами.  
  
-   Напрямую внедрить в отчет код, написанный на [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] . Если код ссылается на классы платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , не принадлежащие пространству имен <xref:System.Math> или <xref:System.Convert>, то в отчет нужно добавить ссылку. Дополнительные сведения см. в разделе [Добавление в отчет ссылки на сборку (службы SSRS)](add-an-assembly-reference-to-a-report-ssrs.md). Дополнительные сведения о других ссылках, которые можно выполнить из кода, см. в разделе [Пользовательский код и ссылки на сборки в выражениях в конструкторе отчетов (службы SSRS)](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
-   Предоставить сборку пользовательского кода, использующего платформу [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Если предоставляется пользовательская сборка, ее следует установить как на компьютере, на котором создается отчет, так и на сервере отчетов, где выполняется просмотр отчета. Дополнительные сведения см. в статье [Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md).  
  
### <a name="to-add-embedded-code-to-a-report"></a>Добавление в отчет внедренного кода  
  
1.  В режиме **конструктора** щелкните правой кнопкой мыши в области конструктора за границей отчета и выберите команду **Свойства отчета**.  
  
2.  Щелкните **Код**.  
  
3.  В поле **Пользовательский код**введите код. Если при выполнении отчета в коде возникают ошибки, то выводятся предупреждения. В следующем примере создается пользовательская функция с именем `ChangeWord` , заменяющая слово «`Bike`» словом «`Bicycle`».  
  
    ```  
    Public Function ChangeWord(ByVal s As String) As String  
       Dim strBuilder As New System.Text.StringBuilder(s)  
       If s.Contains("Bike") Then  
          strBuilder.Replace("Bike", "Bicycle")  
          Return strBuilder.ToString()  
          Else : Return s  
       End If  
    End Function  
    ```  
  
4.  В следующем примере показывается, как с помощью выражения передать этой функции поле набора данных с именем «Категория».  
  
    ```  
    =Code.ChangeWord(Fields!Category.Value)  
    ```  
  
     Если поместить такое выражение в ячейку таблицы, отображающую значения категории, то при возникновении в поле набора данных для данной строки слова «Bike», в качестве значения ячейки таблицы будет отображено слово «Bicycle».  
  
## <a name="see-also"></a>См. также  
 [Диалоговое окно «Свойства отчета» — «Код»](../report-properties-dialog-box-code.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [Ссылки на коллекцию параметров (построитель отчетов и службы SSRS)](built-in-collections-parameters-collection-references-report-builder.md)  
  
  
