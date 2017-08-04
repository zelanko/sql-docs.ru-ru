---
title: "Изменение сущности (Master Data Services) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- entities [Master Data Services], changing name
ms.assetid: 6a5b9f14-6dfc-49d7-a771-e96461d4feae
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1364db68abbbff7ff13899180af78dc87478737d
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="edit-an-entity-master-data-services"></a>Изменение сущности (Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно изменить сущность.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
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
  
 ![Значок для обновления состояния](../master-data-services/media/mds-statusicon-updating.png "значок для обновления состояния")  
  
 При наличии ошибок во время создания или изменения сущности появится следующее изображение.  
  
 ![Значок состояния ошибки](../master-data-services/media/mds-statusicon-error.png "значок состояния ошибки")  
  
 Если ее состояние нормальное, появится следующее изображение.  
  
 ![Значок состояния ОК](../master-data-services/media/mds-statusicon-ok.png "значок состояния ОК")  
  
## <a name="see-also"></a>См. также:  
 [Явные иерархии (службы Master Data Services)](../master-data-services/explicit-hierarchies-master-data-services.md)   
 [Удалить сущности &#40; Службы Master Data Services &#41;](../master-data-services/delete-an-entity-master-data-services.md)   
 [Сущности (службы Master Data Services)](../master-data-services/entities-master-data-services.md)  
  
  
