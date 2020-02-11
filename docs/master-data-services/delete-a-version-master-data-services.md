---
title: Удаление версии
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- versions [Master Data Services], deleting
- deleting versions [Master Data Services]
ms.assetid: 2a4eeffe-8379-4744-ad44-c27d8c8ac9a8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8ac756143790e8d6c9494489438157ee44c02d06
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728347"
---
# <a name="delete-a-version-master-data-services"></a>Удаление версии (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]версия удаляется тогда, когда связанные с ней основные данные больше не нужны. После удаления версии связанные с ней основные данные больше нельзя получить.  
  
> [!WARNING]  
>  После удаления единственной версии модели она станет непригодной к использованию.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   пользователь должен иметь разрешения на просмотр представления mdm.viw_SYSTEM_SCHEMA_VERSION и на выполнение хранимой процедуры mds.udpVersionDelete в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Дополнительные сведения см. в разделе [Защита объектов базы данных (службы Master Data Services)](../master-data-services/database-object-security-master-data-services.md).  
  
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
 [Версии &#40;Master Data Services&#41;](../master-data-services/versions-master-data-services.md)   
 [Копирование Master Data Services &#40;версии&#41;](../master-data-services/copy-a-version-master-data-services.md)  
  
  
