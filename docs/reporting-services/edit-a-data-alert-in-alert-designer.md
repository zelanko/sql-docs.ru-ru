---
title: Изменение предупреждения о данных в конструкторе предупреждений | Документы Майкрософт
ms.date: 07/02/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- editing, data alerts
- updating, data alerts
- editing, alerts
- updating, alerts
ms.assetid: dde3664d-90b5-4b12-969e-39152c86e58a
author: maggiesMSFT
ms.author: maggies
monikerRange: '>=sql-server-2016 <=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: c3a2f7a889d856e589a3471eadc74f5bc9010c5d
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "65571521"
---
# <a name="edit-a-data-alert-in-alert-designer"></a>изменить предупреждение в конструкторе предупреждений

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016](../includes/ssrs-appliesto-2016.md)] [!INCLUDE [ssrs-appliesto-not-2017](../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../includes/ssrs-previous-versions.md)]

Если вы хотите изменить определение предупреждения об изменении данных, его следует открыть в диспетчере предупреждений об изменении данных. Изменить определение предупреждения может только пользователь, который его создал. Дополнительные сведения об открытии диспетчера предупреждений данных см. в разделе [Управление предупреждениями данных в диспетчере предупреждений данных](../reporting-services/manage-my-data-alerts-in-data-alert-manager.md).

> [!NOTE]
> Интеграция служб Reporting Services с SharePoint больше не доступна после выхода SQL Server 2016.

 На следующем рисунке показано контекстное меню предупреждения об изменении данных в диспетчере предупреждений об изменении данных.  
  
 ![Открытие конструктора предупреждений о данных нажатием кнопки "Правка"](../reporting-services/media/rs-alertmanageriwopendesigner.gif "Открытие конструктора предупреждений о данных нажатием кнопки "Правка"")  
  
 Следующая процедура включает в себя шаги по открытию определения предупреждения для изменения в конструкторе предупреждений об изменении данных из диспетчера предупреждений об изменении данных.  
  
### <a name="to-edit-a-data-alert-definition-in-data-alert-designer"></a>Редактирование определения предупреждения об изменении данных в конструкторе предупреждений об изменении данных.  
  
1.  Щелкните правой кнопкой мыши определение предупреждения об изменении данных, которое требуется изменить в диспетчере предупреждений об изменении данных, и выберите команду **Изменить**.  
  
     Определение предупреждения откроется в конструкторе предупреждений об изменении данных.  
  
2.  Обновите правила, параметры расписания и параметры электронной почты. Дополнительные сведения см. в разделах [Конструктор предупреждений данных](../reporting-services/data-alert-designer.md) и [Создание предупреждения данных в конструкторе предупреждений данных](../reporting-services/create-a-data-alert-in-data-alert-designer.md).  
  
    > [!NOTE]  
    >  Выбрать другой веб-канал данных нельзя. Чтобы использовать другой веб-канал данных, следует создать новое определение предупреждения об изменении данных.  
  
3.  Выберите команду **Сохранить**.  
  
    > [!NOTE]  
    >  Если отчет был изменен и изменились веб-каналы данных, созданные на основе отчета, то определение предупреждения может стать недопустимым. Это происходит, когда столбец, на который ссылается определение предупреждения в своих правилах, удаляется из отчета или меняет тип данных, или если отчет удаляется или перемещается. Недопустимое определение предупреждения можно открыть, но нельзя повторно сохранить до тех пор, пока оно не станет допустимым для текущей версии веб-канала данных отчета, на котором оно основано. Дополнительные сведения о создании веб-каналов данных на основе отчетов см. в разделе [Формирование веб-каналов данных из отчетов (построитель отчетов и службы SSRS)](../reporting-services/report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).  

## <a name="see-also"></a>См. также:

[Диспетчер предупреждений данных для оповещения администраторов](../reporting-services/data-alert-manager-for-alerting-administrators.md)   
[Предупреждения об изменении данных в службах Reporting Services](../reporting-services/reporting-services-data-alerts.md)  

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
