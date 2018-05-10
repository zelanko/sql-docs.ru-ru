---
title: Проверка данных (надстройка MDS для Excel) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.component: microsoft-excel-add-in
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 71eda98f-01a4-4fff-8246-be3133782523
caps.latest.revision: 9
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: ab8cf0017260edd45a7538191689cd47198f8a05
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="validating-data-mds-add-in-for-excel"></a>Проверка данных (надстройка MDS для Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]при публикации данных происходят проверки двух типов:  
  
-   К данным применяются все определенные бизнес-правила.  
  
-   Данные проверяются на допустимость в качестве значений атрибута (например, у них должно быть определенные количество знаков или тип данных).  
  
 В обоих случаях допустимые данные публикуются в репозитории MDS. Недопустимые данные выделяются, а в столбцах состояния могут отображаться сведения об ошибке.  
  
## <a name="when-validation-occurs"></a>Когда осуществляется проверка  
 В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]проверка происходит при публикации новых или измененных данных, а также при применении бизнес-правил вручную.  
  
 Если проверка с использованием бизнес-правил не прошла, данные все равно публикуются в репозитории MDS. Если входные данные не проходят проверку, они не публикуются в репозитории.  
  
## <a name="validation-statuses"></a>Состояния проверки  
 В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]возможны приведенные ниже состояния проверки.  
  
 Сведения о дополнительных предварительных условиях см. в разделе [Состояния проверки (службы Master Data Services)](../../master-data-services/validation-statuses-master-data-services.md).  
  
|Состояние|Description|  
|------------|-----------------|  
|Проверка завершена с ошибкой.|Одно или несколько значений в строке не прошли проверку с использованием бизнес-правил, определенных администратором MDS.|  
|Проверка завершена успешно|Все значения в строке прошли проверку с использованием бизнес-правил.|  
  
## <a name="input-statuses"></a>Состояния входных данных  
 В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]возможны приведенные ниже состояния входных данных.  
  
|Состояние|Description|  
|------------|-----------------|  
|Ошибка|Одно или несколько значений в строке не соответствуют системным требованиям, таким как длина или тип данных. Значение не обновляется в репозитории MDS.|  
|Новая строка|Значения в строке еще не опубликованы в репозитории MDS.|  
|Только для чтения|Вошедший в систему пользователь имеет разрешения «Только для чтения» на одно или несколько значений в строке, и значения нельзя обновить.|  
|Без изменений|Ни одно значение в строке на листе не было изменено. Это не означает, что значения в хранилище не изменились. Чтобы получить последние данные на листе, в группе **Подключение и загрузка** нажмите кнопку **Загрузить или обновить**.<br /><br /> Это параметр по умолчанию для каждой строки.|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Определяет, какие значения не соответствуют определенным бизнес-правилам.|[Применение бизнес-правил (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/apply-business-rules-mds-add-in-for-excel.md)|  
|Чтобы исправить ошибки проверки, просмотрите все транзакции, выполненные для элемента.|[Просмотр всех заметок или транзакций для элемента (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Обзор импорта данных из Excel (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
