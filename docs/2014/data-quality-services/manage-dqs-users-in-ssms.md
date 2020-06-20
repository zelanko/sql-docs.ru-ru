---
title: Управление пользователями DQS в SSMS | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 955af01d-00da-4c51-9311-f3848749df54
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bf4cd7cfb635aa990cbabab37905dd640f9e69fe
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937515"
---
# <a name="manage-dqs-users-in-ssms"></a>Управление пользователями DQS в среде SSMS
  В этом разделе описывается создание дополнительных пользователей в экземпляре SQL Server с помощью SQL Server Management Studio, а также предоставление соответствующих ролей [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) в базе данных DQS_MAIN.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Учетная запись пользователя Windows должна быть членом соответствующей предопределенной роли сервера (например, securityadmin, serveradmin или sysadmin) для создания имен входа SQL Server и предоставления соответствующих ролей DQS.  
  
##  <a name="create-a-sql-login-and-grant-dqs-role"></a><a name="GrantRoles"></a>Создание имени входа SQL и предоставление роли DQS  
  
1.  Запустите среду Microsoft SQL Server Management Studio.  
  
2.  В среде Microsoft SQL Server Management Studio разверните экземпляр SQL Server, а затем разверните **Безопасность**.  
  
3.  Щелкните папку **Безопасность** правой кнопкой мыши, наведите указатель на пункт **Создать**и выберите пункт **Имя входа**.  
  
4.  В диалоговом окне **Создание имени входа** укажите имя пользователя Windows в поле **Имя для входа**, выберите тип проверки подлинности **Проверка подлинности Windows** и нажмите кнопку **Поиск** для проверки пользователя.  
  
    > [!NOTE]  
    >  Службы DQS поддерживают только проверку подлинности Windows. Проверка подлинности SQL Server не поддерживается.  
  
5.  После проверки пользователя щелкните страницу **Сопоставление пользователей** в левой части окна.  
  
6.  В правой области установите флажок в столбце **Сопоставление** для базы данных **DQS_MAIN** , а затем на панели **Членство в роли базы данных для: DQS_MAIN**установите флажок **dqs_administrator**, **dqs_kb_editor** или **dqs_kb_operator** в зависимости от уровня доступа, который требуется пользователю.  
  
7.  В диалоговом окне **Создание имени входа** нажмите кнопку **ОК**, чтобы применить изменения.  
  
    > [!NOTE]  
    >  Если пользователю предоставляется роль **dqs_administrator** , примените изменения, а затем повторно проверьте разрешения пользователя; флажки двух других ролей DQS (**dq_kb_editor** и **dqs_kb_operator**) также должны быть установлены.  
  
  
