---
title: Общие сведения. Импорт данных из Excel (надстройка MDS для Excel) | Документация Майкрософт
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: ea84a9aa-aeec-411b-ab8d-bc1b14f864a3
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 6a43eb9fbf6877a43454e85bf59f97b4650e96ae
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65481169"
---
# <a name="overview-importing-data-from-excel-mds-add-in-for-excel"></a>Общие сведения. Импорт данных из Excel (надстройка MDS для Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]можно опубликовать данные в репозитории MDS, если их необходимо передать другим пользователям. После публикации они станут доступными для загрузки другим пользователям надстройки.  
  
 Все добавленные и обновившиеся при публикации данные публикуются в репозитории MDS. Удаленные данные не публикуются, их необходимо удалить отдельно. Дополнительные сведения см. в разделе [Удаление строки (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/delete-a-row-mds-add-in-for-excel.md).  
  
> [!NOTE]  
>  Публикация не может быть использована для создания новой сущности. Дополнительные сведения о создании сущностей см. в разделе [Создание сущности (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/create-an-entity-mds-add-in-for-excel.md).  
  
## <a name="when-multiple-users-publish-at-the-same-time"></a>Одновременная публикация несколькими пользователями  
 Несколько пользователей могут публиковать обновления одних и тех же данных одновременно. В результате каждой публикации в базу данных записывается обновление. Это означает, что пользователь, не имеющий самых последних обновленных данных, может изменять значения во время публикации.  
  
 В базе данных публикуются только внесенные вами изменения. Устаревшие данные на листе не публикуются.  
  
## <a name="transactions-and-annotations"></a>Транзакции и заметки  
 Каждое опубликованное изменение сохраняется в виде транзакции. По вашему выбору в транзакцию можно добавить заметки (комментарии), объясняющие причины внесения изменений.  
  
-   Заметки к операциям удаления не добавляются, хотя они сохраняются в виде транзакций, которые могут использоваться для выполнения обратной операции администратором.  
  
-   Если для элемента изменить значение поля **Код** , то все предыдущие транзакции для этого элемента будут недоступны. Вернув для поля **Код** исходное значение, вы сможете получить доступ к предыдущим транзакциям.  
  
-   Можно просмотреть транзакции для элемента, сделанные другими пользователями. Можно также просмотреть все свои транзакции для элемента, даже если вы больше не имеете разрешений на определенные атрибуты. Транзакции, включающие атрибуты, для которых установлено разрешение "Запретить", просмотреть нельзя.  
  
 Можно просмотреть все транзакции, выполненные для элемента. Дополнительные сведения см. в разделе [Просмотр всех заметок или транзакций для элемента (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md).  
  
> [!IMPORTANT]  
>  Если введена заметка длиной более 500 символов, то она автоматически усекается.  
  
## <a name="business-rule-and-other-validation"></a>Проверка бизнес-правил и другие проверки  
 При публикации данных выполняется проверка, чтобы обеспечить точность данных перед их добавлением в репозиторий MDS. Если данные не соответствуют заданным условиям, то они не будут опубликованы. Дополнительные сведения см. в разделе [Проверка данных (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/validating-data-mds-add-in-for-excel.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Публикация данных из активного листа в репозитории MDS.|[Импорт данных из Excel в службы Master Data Services (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)|  
|Одновременное удаление строки из репозитория MDS и с листа.|[Удаление строки (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/delete-a-row-mds-add-in-for-excel.md)|  
|Просмотр заметок (комментариев) и транзакций для строк данных (элементов), когда необходимо просмотреть, как менялись данные во времени.|[Просмотр всех заметок или транзакций для элемента (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)|  
|Объединение данных из двух листов, чтобы сравнить их перед публикацией.|[Объединение данных (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/combine-data-mds-add-in-for-excel.md)|  

  
## <a name="related-content"></a>См. также  
  
-   [Обновление данных (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/refreshing-data-mds-add-in-for-excel.md)  
  
-   [Надстройка Master Data Services для Microsoft Excel](../../master-data-services/microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)  
  
  
