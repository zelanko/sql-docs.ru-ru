---
title: 'Урок 6: Выполнение приложения RDL-схемы (VB-C#) | Документы Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2cd2386-2df8-4b69-ab81-9ad1a31f6d27
caps.latest.revision: 15
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 95ef194a66d6c5480f8a83cbd0b78547e79804e6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192575"
---
# <a name="lesson-6-run-the-rdl-schema-application-vb-c"></a>Урок 6: Выполнение приложения RDL-схемы (VB-C#)
  В среде [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] доступно два способа построения и выполнения приложения командной строки из интегрированной среды разработки:  
  
-   запустить (с отладкой);  
  
-   запустить без отладки.  
  
### <a name="to-build-and-run-the-samplerdlschema-application"></a>Сборка и запуск приложения SampleRDLSchema  
  
1.  В меню **Debug** выберите команду **Start Without Debugging**. При выборе этой команды окно консоли останется открытым после того, как программа завершит свою работу.  
  
     Приложение выводит на консоль следующие данные:  
  
    ```  
    Loading Report Definition  
    Updating Report Definition  
    - Old Description: <Old Report Description>  
    - New Description: <New Report Description>  
    Publishing Report Definition  
    ```  
  
2.  Чтобы закрыть консоль, нажмите любую кнопку.  
  
    > [!NOTE]  
    >  Сведения обо всех возникающих ошибках выводятся на консоль.  
  
3.  Когда образец приложения закончит выполнение, на сервере отчетов будет сохранена обновленная копия отчета.  
  
## <a name="see-also"></a>См. также  
 [Обновление отчетов с помощью классов, созданных из RDL-схемы &#40;учебник по службам SSRS&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [Язык определения отчетов (службы SSRS)](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  