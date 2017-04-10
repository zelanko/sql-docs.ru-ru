---
title: "Customize the Parameters Pane in a Report (Report Builder) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4ce9e8d5-911a-4422-928f-a8d005b79fc6
caps.latest.revision: 8
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 8
---
# Customize the Parameters Pane in a Report (Report Builder)
  При создании отчетов с разбиением на страницы с параметрами в построителе отчетов можно настроить область параметров. В перенаселении конструктора отчетов можно перетащить параметр в конкретный столбец и строку на панели параметров. Для изменения макета панели столбцы можно добавлять и удалять.  
  
 При перетаскивании параметра в новый столбец или строку на панели также изменяется порядок параметров в области **Данные отчета**. При изменении порядка параметров в области **Данные отчета** меняется расположение параметра на панели. Дополнительные сведения о том, почему важен порядок параметров, см. в разделе [Изменение порядка параметров отчета (построитель отчетов и службы SSRS)](../../reporting-services/report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md).  
  
## Настройка области параметров  
  
1.  Чтобы отобразить область параметров, на вкладке **Представление** установите флажок **Параметры** .  
  
     ![Access parameters pane from View tab](../../reporting-services/report-design/media/ssrs-customparameter-accessparameterpanedesignmode.png "Access parameters pane from View tab")  
  
     Панель отобразится в верхней части области конструктора.  
  
2.  Чтобы добавить параметр на панель, выполните одно из следующих действий.  
  
    -   Щелкните правой кнопкой мыши пустую ячейку в области параметров, а затем нажмите кнопку **Добавить параметр**.  
  
         ![Add new parameter from parameters pane](../../reporting-services/report-design/media/ssrs-customizeparameter-addnewparameter.png "Add new parameter from parameters pane")  
  
    -   Щелкните правой кнопкой мыши **Параметры** в области **Данные отчета** , а затем нажмите кнопку **Добавить параметр**.  
  
3.  Чтобы переместить параметр в новое расположение в области параметров, перетащите его в другую ячейку панели.  
  
     При изменении расположения параметра в области порядок параметров в списке **Параметры** в области **Данные отчета** меняется автоматически. Дополнительные сведения о влиянии порядка параметров см. в разделе [Изменение порядка параметров отчета (построитель отчетов и службы SSRS)](../../reporting-services/report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md).  
  
4.  Для получения доступа к свойствам параметра выполните одно из следующих действий.  
  
    -   Щелкните правой кнопкой мыши параметр в области параметров и выберите **Свойства параметра**.  
  
         ![Access parameter properties from the parameters pane](../../reporting-services/report-design/media/ssrs-customizeparameter-accessparameterproperties-composite.png "Access parameter properties from the parameters pane")  
  
    -   В области **Данные отчета** , а затем нажмите кнопку **Свойства параметра**.  
  
5.  Чтобы добавить в область новые столбцы и строки или удалить существующие строки и столбцы, щелкните правой кнопкой мыши область параметров и в отобразившемся меню выберите команду.  
  
     ![Add columns and rows to the parameters pane](../../reporting-services/report-design/media/ssrs-customparameter-addcolumnsrows.png "Add columns and rows to the parameters pane")  
  
    > [!IMPORTANT]  
    >  Если удалить столбец или строку, содержащие параметры, эти параметры будут удалены из отчета.  
  
6.  Чтобы удалить параметр с панели и из отчета, выполните одно из следующих действий.  
  
    -   В области параметров щелкните правой кнопкой мыши параметр и нажмите кнопку  **Удалить**.  
  
         ![Delete parameters from the parameters pane](../../reporting-services/report-design/media/ssrs-customparameter-deleteparameter.png "Delete parameters from the parameters pane")  
  
    -   В области **Данные отчета** , а затем нажмите кнопку **Удалить**.  
  
## См. также  
 [Параметры отчета (построитель отчетов и конструктор отчетов)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)  
  
  