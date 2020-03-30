---
title: Включение удаленного издателя на распространителе (SSMS)
description: Узнайте, как включить удаленный издатель на распространителе с помощью SQL Server Management Studio (SSMS).
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- remote Distributors [SQL Server replication]
- Publishers [SQL Server replication]
ms.assetid: 6f8e2831-5c45-4e39-8e51-d37e2813cf3d
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 59c70e5732ea8968798f3a54b246befe73d3fcb0
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "76288081"
---
# <a name="enable-a-remote-publisher-at-a-distributor-sql-server-management-studio"></a>включить удаленный издатель на распространителе (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Предоставьте издателю разрешение использовать удаленный распространитель на странице **Издатели** . Эта страница доступна в мастере настройки распространителя и в диалоговом окне **Свойства распространителя — \<распространитель>** . Дополнительные сведения об использовании мастера и о доступе к этому диалоговому окну см. в статьях [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md) и [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-enable-a-publisher-in-the-configure-distribution-wizard"></a>Включение издателя в мастере настройки распространителя  
  
1.  На странице **Издатели** мастера настройки распространителя щелкните **Добавить**.  
  
2.  Щелкните **Добавить издатель SQL Server**. Сведения о том, как разрешить издателю Oracle использовать распространитель, см. в разделе [Create a Publication from an Oracle Database](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md).  
  
3.  В диалоговом окне **Соединение с сервером** укажите сведения о соединении для издателя, который будет использовать удаленный распространитель, а затем щелкните **Соединить**.  
  
4.  На странице **Пароль распространителя** в текстовых полях **Пароль** и **Подтверждение пароля** укажите надежный пароль для учетной записи **distributor_admin** , используемой системой репликации, чтобы подключить издателя к распространителю для выполнения административных задач.  
  
5.  Для просмотра и изменения параметров издателя нажмите кнопку свойств с многоточием ( **…** ).  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

### <a name="to-enable-a-publisher-in-the-distributor-properties-dialog-box"></a>Включение издателя в диалоговом окне «Свойства распространителя»  
  
1.  На странице **Издатели** диалогового окна **Свойства распространителя — \<распространитель>** нажмите кнопку **Добавить**.  
  
2.  Щелкните **Добавить издатель SQL Server**. Сведения о том, как разрешить издателю Oracle использовать распространитель, см. в разделе [Create a Publication from an Oracle Database](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md).  
  
3.  В диалоговом окне **Соединение с сервером** укажите сведения о соединении для издателя, который будет использовать удаленный распространитель, а затем щелкните **Соединить**.  
  
4.  На странице **Издатели** в текстовых полях **Пароль** и **Подтверждение пароля** укажите надежный пароль для учетной записи **distributor_admin** , используемой системой репликации, чтобы подключить издатель к распространителю для выполнения административных задач.  
  
5.  Для просмотра и изменения параметров издателя нажмите кнопку свойств с многоточием ( **…** ).  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Настройка распространения](../../relational-databases/replication/configure-distribution.md)   
 [Защита распространителя](../../relational-databases/replication/security/secure-the-distributor.md)  
  
  
