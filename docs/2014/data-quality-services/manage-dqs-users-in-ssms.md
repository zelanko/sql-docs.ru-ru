---
title: Управление пользователями DQS в среде SSMS | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 955af01d-00da-4c51-9311-f3848749df54
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d17883d39f4579f509eed894735c676f464feeeb
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2018
ms.locfileid: "51032189"
---
# <a name="manage-dqs-users-in-ssms"></a>Управление пользователями DQS в среде SSMS
  В этом разделе описывается создание дополнительных пользователей в экземпляре SQL Server с помощью SQL Server Management Studio, а также предоставление соответствующих ролей [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) в базе данных DQS_MAIN.  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Учетная запись пользователя Windows должна быть членом соответствующей предопределенной роли сервера (например, securityadmin, serveradmin или sysadmin) для создания имен входа SQL Server и предоставления соответствующих ролей DQS.  
  
##  <a name="GrantRoles"></a> Создайте имя входа SQL и предоставление ролей DQS  
  
1.  Запустите среду Microsoft SQL Server Management Studio.  
  
2.  В среде Microsoft SQL Server Management Studio разверните экземпляр SQL Server, а затем разверните **Безопасность**.  
  
3.  Щелкните папку **Безопасность** правой кнопкой мыши и выберите пункт **Создать**, а затем — **Имя входа**.  
  
4.  В диалоговом окне **Создание имени входа** укажите имя пользователя Windows в поле **Имя входа** , выберите для типа проверки подлинности **Проверка подлинности Windows**и нажмите кнопку **Поиск** для проверки пользователя.  
  
    > [!NOTE]  
    >  Службы DQS поддерживают только проверку подлинности Windows. Проверка подлинности SQL Server не поддерживается.  
  
5.  После проверки пользователя щелкните страницу **Сопоставление пользователей** в левой части окна.  
  
6.  В правой части окна установите флажок в столбце **Сопоставление** для базы данных **DQS_MAIN** , а затем установите флажок **dqs_administrator**, **dqs_kb_editor**или **dqs_kb_operator** на панели **Членство в роли базы данных для: DQS_MAIN** , в зависимости от уровня доступа, который требуется данному пользователю.  
  
7.  В диалоговом окне **Создание имени входа** нажмите кнопку **ОК** , чтобы применить изменения.  
  
    > [!NOTE]  
    >  Если пользователю предоставляется роль **dqs_administrator** , примените изменения, а затем повторно проверьте разрешения пользователя; флажки двух других ролей DQS (**dq_kb_editor** и **dqs_kb_operator**) также должны быть установлены.  
  
  
