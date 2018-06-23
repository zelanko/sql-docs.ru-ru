---
title: Создание и изменение группы серверов (SQL Server Management Studio) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.editgroup.f1
- sql12.swb.newgroup.f1
helpviewer_keywords:
- Registered Servers [SQL Server], server groups
- server groups [SQL Server]
- groups [SQL Server], server
ms.assetid: d4a942bd-2dd1-42db-ad0e-e9a9ae5b856d
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bdec272826760d43ef15067794d18d6602659b70
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180177"
---
# <a name="create-or-edit-a-server-group-sql-server-management-studio"></a>Создание или изменение группы серверов (среда SQL Server Management Studio)
  В этом разделе описывается организация серверов в компоненте «Зарегистрированные серверы» в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] путем создания групп серверов и помещения серверов в эти группы. Группы серверов в зарегистрированных серверах можно создавать в любое время, либо делать это при их регистрации.  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-create-a-server-group-in-registered-servers"></a>Создание группы серверов в зарегистрированных серверах  
  
1.  В окне «Зарегистрированные серверы» выберите обозначение типа сервера на панели инструментов зарегистрированных серверов. Если окно «Зарегистрированные серверы» не отображается, выберите **Зарегистрированные серверы** в меню **Вид** .  
  
2.  Щелкните правой кнопкой сервер или группу серверов, выберите пункт **Создать**и щелкните **Группа серверов**.  
  
3.  В диалоговом окне **Создание группы серверов** перейдите к полю со списком **Имя группы** и введите уникальное имя для группы серверов. Имя группы серверов должно быть уникальным для текущего места в дереве «Зарегистрированные серверы».  
  
4.  В поле со списком **Описание группы** введите понятное имя, описывающее группу серверов, например «Финансовые серверы в Латинской Америке».  
  
5.  В поле **Выберите место размещения новой группы серверов** выберите размещение группы и нажмите **Сохранить**.  
  
    > [!NOTE]  
    >  Также можно создать новую группу серверов при регистрации сервера. Для этого нажмите кнопку **Создать группу**и заполните параметры в диалоговом окне **Новая группа** .  
  
## <a name="see-also"></a>См. также  
 [Регистрация серверов](register-servers.md)  
  
  