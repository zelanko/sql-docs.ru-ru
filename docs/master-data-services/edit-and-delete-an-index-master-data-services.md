---
title: "Изменение и удаление индекса (службы Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8fb2a63-f9ae-4b9d-b26f-2024d9af15c5
caps.latest.revision: "5"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c46e03e62200624211c0db1d5aa652d03f56beaf
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="edit-and-delete-an-index-master-data-services"></a>Изменение и удаление индекса (Master Data Services)
  Индекс, созданный для атрибутов, можно изменить или удалить.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   Иметь разрешение на доступ к функциональной области "Администрирование системы". Дополнительные сведения см. в разделе [Разрешения функциональной области (службы Master Data Services)](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
 **Изменение индекса**  
  
1.  В диспетчере основных данных щелкните **Системное администрирование**.  
  
2.  На странице **Manage Model** (Управление моделью) выберите в сетке модель и щелкните **Сущности**.  
  
3.  На странице **Manage Entity** (Управление сущностью) в сетке выберите сущность, содержащую индекс, который нужно изменить.  
  
4.  Щелкните **Индексы**.  
  
5.  На странице **Manage Index** (Управление индексом) выберите индекс, который нужно изменить, и щелкните **Изменить**.  
  
6.  Введите новое имя индекса в поле **Имя** .  
  
7.  Установите или снимите флажок **IsUnique** .  
  
8.  Измените список назначенных атрибутов, добавив атрибуты в список или удалив их оттуда.  
  
9. Нажмите кнопку **Сохранить**.  
  
 **Удаление индекса**  
  
1.  На странице **Manage Model** (Управление моделью) выберите в сетке модель и щелкните **Сущности**.  
  
2.  На странице **Manage Entity** (Управление сущностью) в сетке выберите сущность, содержащую индекс, который нужно удалить.  
  
3.  Щелкните **Индексы**.  
  
4.  На странице **Manage Index** (Управление индексом) выберите индекс, который нужно удалить, и щелкните **Удалить**.  
  
5.  В окнах подтверждения нажимайте кнопку **ОК**.  
  
## <a name="see-also"></a>См. также:  
 [Создание индекса (Master Data Services)](../master-data-services/create-an-index-master-data-services.md)   
 [Пользовательский индекс (Master Data Services)](../master-data-services/custom-index-master-data-services.md)  
  
  
