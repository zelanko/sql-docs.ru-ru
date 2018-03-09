---
title: "Изменение сущности (службы Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- entities [Master Data Services], changing name
ms.assetid: 6a5b9f14-6dfc-49d7-a771-e96461d4feae
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 80bb4a70c306371910e0059c2d9bbb7a7330d617
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2018
---
# <a name="edit-an-entity-master-data-services"></a>Изменение сущности (Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно изменить сущность.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-edit-an-entity"></a>Изменение сущности  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Manage Model** (Управление моделью) выберите в сетке модель и щелкните **Сущности**.  
  
3.  На странице **Manage Entity** (Управление сущностью) в сетке выберите строку сущности, которую нужно изменить, а затем щелкните **Изменить**.  
  
4.  Введите измененное имя сущности в поле **Имя** .  
  
5.  В поле **Описание** введите измененное описание сущности.  
  
6.  В поле **Имя для промежуточных таблиц** введите измененное имя промежуточной таблицы.  
  
7.  В поле **Тип журнала транзакций** из раскрывающегося списка выберите измененный тип журнала транзакций.  
  
     Дополнительные сведения см. в разделе [Изменение типа журнала транзакций сущности (Master Data Services)](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)  
  
8.  Установите или снимите флажок **Автоматически создавать значения кода** .  
  
     Дополнительные сведения см. в разделе [Автоматическое создание кодов (службы Master Data Services)](../master-data-services/automatic-code-creation-master-data-services.md)  
  
9. Установите или снимите флажок **Включить сжатие данных** . Сжатие строк включено по умолчанию.  
  
     Дополнительные сведения см. в разделе [Data Compression](../relational-databases/data-compression/data-compression.md).  
  
## <a name="status"></a>Состояние  
 В столбце состояния в сетке отображается состояние операции с сущностью. После нажатия кнопки **Сохранить сущность**появится следующее изображение, которое указывает на то, что сущность обновляется.  
  
 ![Значок обновления состояния](../master-data-services/media/mds-statusicon-updating.png "Значок обновления состояния")  
  
 При наличии ошибок во время создания или изменения сущности появится следующее изображение.  
  
 ![Значок состояния ошибки](../master-data-services/media/mds-statusicon-error.png "Значок состояния ошибки")  
  
 Если ее состояние нормальное, появится следующее изображение.  
  
 ![Значок нормального состояния](../master-data-services/media/mds-statusicon-ok.png "Значок нормального состояния")  
  
## <a name="see-also"></a>См. также:  
 [Явные иерархии (службы Master Data Services)](../master-data-services/explicit-hierarchies-master-data-services.md)   
 [Удаление сущности (службы Master Data Services)](../master-data-services/delete-an-entity-master-data-services.md)   
 [Сущности (службы Master Data Services)](../master-data-services/entities-master-data-services.md)  
  
  
