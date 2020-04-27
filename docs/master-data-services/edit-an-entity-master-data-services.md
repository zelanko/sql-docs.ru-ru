---
title: Изменение сущности
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], changing name
ms.assetid: 6a5b9f14-6dfc-49d7-a771-e96461d4feae
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4329f618b812bb566d974c5434ef0362b1383f2d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "73729297"
---
# <a name="edit-an-entity-master-data-services"></a>Изменение сущности (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно изменить сущность.  
  
## <a name="prerequisites"></a>Предварительные условия  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** .  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-edit-an-entity"></a>Изменение сущности  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Управление моделью** выберите модель в сетке и щелкните **сущности**.  
  
3.  На странице **Manage Entity** (Управление сущностью) в сетке выберите строку сущности, которую нужно изменить, а затем щелкните **Изменить**.  
  
4.  Введите измененное имя сущности в поле **Имя** .  
  
5.  В поле **Описание** введите измененное описание сущности.  
  
6.  В поле **Имя для промежуточных таблиц** введите измененное имя промежуточной таблицы.  
  
7.  В поле **Тип журнала транзакций** из раскрывающегося списка выберите измененный тип журнала транзакций.  
  
     Дополнительные сведения см. в разделе [Изменение типа журнала транзакций сущности (Master Data Services)](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)  
  
8.  Установите или снимите флажок **Автоматически создавать значения кода** .  
  
     Дополнительные сведения см. в разделе [Автоматическое создание кодов (службы Master Data Services)](../master-data-services/automatic-code-creation-master-data-services.md)  
  
9. Установите или снимите флажок **Включить сжатие данных** . Сжатие строк включено по умолчанию.  
  
     Дополнительные сведения см. в разделе [Сжатие данных](../relational-databases/data-compression/data-compression.md) .  
  
## <a name="status"></a>Состояние  
 В столбце состояния в сетке отображается состояние операции с сущностью. После нажатия кнопки **Сохранить сущность**появится следующее изображение, которое указывает на то, что сущность обновляется.  
  
 ![Значок обновления состояния](../master-data-services/media/mds-statusicon-updating.png "Значок обновления состояния")  
  
 При наличии ошибок во время создания или изменения сущности появится следующее изображение.  
  
 ![Значок состояния ошибки](../master-data-services/media/mds-statusicon-error.png "Значок состояния ошибки")  
  
 Если ее состояние нормальное, появится следующее изображение.  
  
 ![Значок состояния "ОК"](../master-data-services/media/mds-statusicon-ok.png "Значок состояния "ОК"")  
  
## <a name="see-also"></a>См. также  
 [Явные иерархии &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)   
 [Удаление сущности &#40;Master Data Services&#41;](../master-data-services/delete-an-entity-master-data-services.md)   
 [Сущности (службы Master Data Services)](../master-data-services/entities-master-data-services.md)  
  
  
