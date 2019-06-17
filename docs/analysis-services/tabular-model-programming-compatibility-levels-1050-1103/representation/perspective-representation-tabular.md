---
title: Представление перспективы (табличное) | Документация Майкрософт
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8ee406b4a5f1f9e366457ac150f10da226551f79
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63019312"
---
# <a name="perspective-representation-tabular"></a>Представление перспективы (табличное)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Перспектива представляет собой механизм упрощения или фокусировки модели в меньшую ее часть для клиентского приложения.  
  
 См. в разделе [представление перспективы (табличные данные)](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/perspective-representation-tabular.md) Дополнительные сведения о способах создания и управления им представление перспективы.  
  
> [!WARNING]  
>  Перспективы не являются механизмом безопасности; к объектам вне перспективы пользователь все равно может получить доступ посредством других интерфейсов.  
  
## <a name="perspective-representation"></a>Представление перспективы  
 С точки зрения объектов AMO представление перспективы имеет связь типа «один к одному» с <xref:Microsoft.AnalysisServices.Perspective> и никакие другие основные объекты AMO не требуются.  
  
### <a name="perspective-in-amo"></a>Перспектива в объектах AMO  
 В следующем фрагменте кода показано, как создать перспективу в табличной модели. Ключевым элементом в этом фрагменте кода является perspectiveElements. Этот объект является графическим представлением всех объектов в табличной модели, которые доступны пользователю. *perspectiveElements* содержит 4 столбца и для этого сценария относятся только те столбцы, 1, 2 и 3. Столбец 1 содержит тип отображаемого элемента -elementTypeValue-. Столбец 2 содержит полное имя элемента --. Скорее всего, понадобится выполнить синтаксический анализ для ввода элемента в перспективу. Столбец 3 содержит элемент флажка -checkedElement-, который сообщает, входит ли элемент в перспективу.  
  
```  
  
private void updatePerspective_Click(  
                     AMO.Cube modelCube  
                  ,  DataGridView perspectiveElements  
                  ,  string updatedPerspectiveID  
             )  
{  
    //Update is done by delete first, create new and insert after  
    //if perspective doesn't exist then create first and insert after  
    updatedPerspectiveID = updatedPerspectiveID.Trim();  
    if (modelCube.Perspectives.Contains(updatedPerspectiveID))  
    {  
        modelCube.Perspectives.Remove(updatedPerspectiveID, true);  
        newDatabase.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.UpdateOrCreate);  
    }  
    AMO.Perspective currentPerspective = modelCube.Perspectives.Add(updatedPerspectiveID, updatedPerspectiveID);  
  
    foreach (DataGridViewRow currentDGVRow in perspectiveElements.Rows)  
    {  
        bool checkedElement = (bool)currentDGVRow.Cells[3].Value;  
        if (checkedElement)  
        {  
            string elementTypeValue = currentDGVRow.Cells[1].Value.ToString();  
            string elementNameValue = currentDGVRow.Cells[2].Value.ToString();  
            switch (elementTypeValue)  
            {  
                case "Column: Attribute":  
                case "Column: Calculated Column":  
                    {  
                        string perspectiveDimensionName = Regex.Match(elementNameValue, @"(?<=')(.*?)(?=')").ToString();  
                        string perspectiveDimensionAttributeName = Regex.Match(elementNameValue, @"(?<=\[)(.*?)(?=\])").ToString();  
                        AMO.PerspectiveDimension currentPerspectiveDimension;  
                        if (!currentPerspective.Dimensions.Contains(perspectiveDimensionName))  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions.Add(perspectiveDimensionName);  
                        }  
                        else  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions[perspectiveDimensionName];  
                        }  
                        if (!currentPerspectiveDimension.Attributes.Contains(perspectiveDimensionAttributeName))  
                        {  
                            currentPerspectiveDimension.Attributes.Add(perspectiveDimensionAttributeName);  
                        }  
                    }  
                    break;  
                case "Hierarchy":  
                    {  
                        string perspectiveDimensionName = Regex.Match(elementNameValue, @"(?<=')(.*?)(?=')").ToString();  
                        string perspectiveDimensionHierarchyName = Regex.Match(elementNameValue, @"(?<=\[)(.*?)(?=\])").ToString();  
                        AMO.PerspectiveDimension currentPerspectiveDimension;  
                        if (!currentPerspective.Dimensions.Contains(perspectiveDimensionName))  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions.Add(perspectiveDimensionName);  
                        }  
                        else  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions[perspectiveDimensionName];  
                        }  
                        if (!currentPerspectiveDimension.Hierarchies.Contains(perspectiveDimensionHierarchyName))  
                        {  
                            currentPerspectiveDimension.Hierarchies.Add(perspectiveDimensionHierarchyName);  
                        }  
                    }  
                    break;  
                case "Measure":  
                    {  
                        string perspectiveMeasureGroupName = Regex.Match(elementNameValue, @"(?<=')(.*?)(?=')").ToString();  
                        string measureName = Regex.Match(elementNameValue, @"(?<=\[)(.*?)(?=\])").ToString();  
                        string perspectiveMeasureName = string.Format("[Measures].[{0}]", measureName);  
                        AMO.PerspectiveCalculation currentPerspectiveCalculation = new AMO.PerspectiveCalculation(perspectiveMeasureName, AMO.PerspectiveCalculationType.Member);  
                        if (!currentPerspective.Calculations.Contains(perspectiveMeasureName))  
                        {  
                            currentPerspective.Calculations.Add(currentPerspectiveCalculation);  
                        }  
                        if (modelCube.MdxScripts["MdxScript"].CalculationProperties.Contains(string.Format("KPIs.[{0}]", measureName)))  
                        {//Current Measure is also a KPI ==> will be added to the KPIs collection of the perspective  
                            AMO.PerspectiveKpi currentPerspectiveKpi = new AMO.PerspectiveKpi(perspectiveMeasureName);  
                            if (!currentPerspective.Kpis.Contains(perspectiveMeasureName))  
                            {  
                                currentPerspective.Kpis.Add(currentPerspectiveKpi);  
                            }  
                        }  
                    }  
                    break;  
                default:  
                    break;  
            }  
        }  
    }  
  
    newDatabase.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.CreateOrReplace);  
    MessageBox.Show(String.Format("Perpective successfully updated."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Information);  
}  
  
```  
  
## <a name="amo2tabular-sample"></a>Образец AMO2Tabular  
 Однако, чтобы получить основные сведения об использовании объектов AMO для создания представлений перспектив и управления ими, ознакомьтесь с исходным кодом примера преобразования объектов AMO в табличную модель. Этот образец доступен на сайте Codeplex. Важное примечание о коде. Код предоставляется только для иллюстрации логических концепций, поясняемых в этом разделе. Его не следует использовать в рабочей среде или для других целей, за исключением учебных.  
  
  
