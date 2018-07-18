---
title: Включение удаленного издателя на распространителе (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- remote Distributors [SQL Server replication]
- Publishers [SQL Server replication]
ms.assetid: 6f8e2831-5c45-4e39-8e51-d37e2813cf3d
caps.latest.revision: 30
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4eb9d96db6687cc76e20f04ee8d067851fedf034
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37349296"
---
# <a name="enable-a-remote-publisher-at-a-distributor-sql-server-management-studio"></a>включить удаленный издатель на распространителе (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Предоставьте издателю разрешение использовать удаленный распространитель на странице **Издатели** . Эта страница доступна в мастере настройки распространителя и в диалоговом окне **Свойства распространителя — \<распространитель>**. Дополнительные сведения об использовании мастера и о доступе к этому диалоговому окну см. в статьях [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md) и [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-enable-a-publisher-in-the-configure-distribution-wizard"></a>Включение издателя в мастере настройки распространителя  
  
1.  На странице **Издатели** мастера настройки распространителя щелкните **Добавить**.  
  
2.  Щелкните **Добавить издатель SQL Server**. Сведения о том, как разрешить издателю Oracle использовать распространитель, см. в разделе [Create a Publication from an Oracle Database](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md).  
  
3.  В диалоговом окне **Соединение с сервером** укажите сведения о соединении для издателя, который будет использовать удаленный распространитель, а затем щелкните **Соединить**.  
  
4.  На странице **Пароль распространителя** в текстовых полях **Пароль** и **Подтверждение пароля** укажите надежный пароль для учетной записи **distributor_admin** , используемой системой репликации, чтобы подключить издателя к распространителю для выполнения административных задач.  
  
5.  Для просмотра и изменения параметров издателя нажмите кнопку с многоточием (**…**).  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-enable-a-publisher-in-the-distributor-properties-dialog-box"></a>Включение издателя в диалоговом окне «Свойства распространителя»  
  
1.  На странице **Издатели** диалогового окна **Свойства распространителя — \<распространитель>** нажмите кнопку **Добавить**.  
  
2.  Щелкните **Добавить издатель SQL Server**. Сведения о том, как разрешить издателю Oracle использовать распространитель, см. в разделе [Create a Publication from an Oracle Database](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md).  
  
3.  В диалоговом окне **Соединение с сервером** укажите сведения о соединении для издателя, который будет использовать удаленный распространитель, а затем щелкните **Соединить**.  
  
4.  На странице **Издатели** в текстовых полях **Пароль** и **Подтверждение пароля** укажите надежный пароль для учетной записи **distributor_admin** , используемой системой репликации, чтобы подключить издатель к распространителю для выполнения административных задач.  
  
5.  Для просмотра и изменения параметров издателя нажмите кнопку с многоточием (**…**).  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Настройка распространения](../../relational-databases/replication/configure-distribution.md)   
 [Защита распространителя](../../relational-databases/replication/security/secure-the-distributor.md)  
  
  
