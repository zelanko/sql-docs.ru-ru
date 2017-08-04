---
title: "Удаление версии (Master Data Services) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- versions [Master Data Services], deleting
- deleting versions [Master Data Services]
ms.assetid: 2a4eeffe-8379-4744-ad44-c27d8c8ac9a8
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bf3a315d60bed733bd2d72cd6ba2317a8ab84ae5
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="delete-a-version-master-data-services"></a>Удаление версии (службы Master Data Services)
  В службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]версия удаляется тогда, когда связанные с ней основные данные больше не нужны. После удаления версии связанные с ней основные данные больше нельзя получить.  
  
> [!WARNING]  
>  После удаления единственной версии модели она станет непригодной к использованию.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   пользователь должен иметь разрешения на просмотр представления mdm.viw_SYSTEM_SCHEMA_VERSION и на выполнение хранимой процедуры mds.udpVersionDelete в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Дополнительные сведения см. в разделе [Защита объектов базы данных (службы Master Data Services)](../master-data-services/database-object-security-master-data-services.md).  
  
### <a name="to-delete-a-version"></a>Удаление версии  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] и установите соединение с экземпляром компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] для базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Откройте представление mdm.viw_SYSTEM_SCHEMA_VERSION.  
  
3.  Найдите удаляемую версию модели и скопируйте значение в поле **ID** .  
  
4.  Создайте новый запрос.  
  
5.  Введите следующий текст, заменив *version_ID* значением, скопированным в шаге 2.  
  
    ```  
    EXEC [mdm].[udpVersionDelete] @Version_ID='version_ID'  
    ```  
  
6.  Выполните запрос.  
  
    > [!NOTE]  
    >  Возможно, придется подождать несколько минут, чтобы изменение отобразилось в веб-приложении.  
  
## <a name="see-also"></a>См. также:  
 [Версии &#40; Службы Master Data Services &#41;](../master-data-services/versions-master-data-services.md)   
 [Копирование версии &#40; Службы Master Data Services &#41;](../master-data-services/copy-a-version-master-data-services.md)  
  
  
