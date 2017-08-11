---
title: "Добавьте код в отчет (SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code [Reporting Services]
- custom code [Reporting Services]
- expressions [Reporting Services], code
- adding code
- reports [Reporting Services], code
ms.assetid: 00ef8fc6-99fe-49b2-8a22-7eb475881dc4
caps.latest.revision: 41
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ae58ddb9260037fafa37263050e55681944738eb
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="add-code-to-a-report-ssrs"></a>Добавление кода в отчет (службы SSRS)
  В любом выражении можно вызвать собственный пользовательский код. Данный код можно предоставить следующими способами.  
  
-   Напрямую внедрить в отчет код, написанный на [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] . Если код ссылается на классы платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , не принадлежащие пространству имен <xref:System.Math> или <xref:System.Convert>, то в отчет нужно добавить ссылку. Дополнительные сведения см. в разделе [Добавление в отчет ссылки на сборку (службы SSRS)](../../reporting-services/report-design/add-an-assembly-reference-to-a-report-ssrs.md). Дополнительные сведения о других ссылках, которые можно выполнить из кода, см. в разделе [Пользовательский код и ссылки на сборки в выражениях в конструкторе отчетов (службы SSRS)](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
-   Предоставить сборку пользовательского кода, использующего платформу [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Если предоставляется пользовательская сборка, ее следует установить как на компьютере, на котором создается отчет, так и на сервере отчетов, где выполняется просмотр отчета. Дополнительные сведения см. в статье [Using Custom Assemblies with Reports](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md).  
  
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
  
## <a name="see-also"></a>См. также раздел  
 [Диалоговое окно свойств отчета, код](http://msdn.microsoft.com/library/955d4b11-17b4-4f1c-9690-6e7af54caea7)   
 [Примеры выражений &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Ссылки на коллекцию параметров &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/built-in-collections-parameters-collection-references-report-builder.md)  
  
  
