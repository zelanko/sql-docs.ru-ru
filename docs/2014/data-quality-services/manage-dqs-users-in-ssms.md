---
title: Управление пользователями DQS в среде SSMS | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 955af01d-00da-4c51-9311-f3848749df54
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: d8d7e0c31b1e022445006598f791716d765b98c9
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56027985"
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
  
3.  Щелкните папку **Безопасность** правой кнопкой мыши, наведите указатель на пункт **Создать**и выберите пункт **Имя входа**.  
  
4.  В диалоговом окне **Создание имени входа** укажите имя пользователя Windows в поле **Имя для входа**, выберите тип проверки подлинности **Проверка подлинности Windows** и нажмите кнопку **Поиск** для проверки пользователя.  
  
    > [!NOTE]  
    >  Службы DQS поддерживают только проверку подлинности Windows. Проверка подлинности SQL Server не поддерживается.  
  
5.  После проверки пользователя щелкните страницу **Сопоставление пользователей** в левой части окна.  
  
6.  В области справа установите флажок в разделе **карты** столбец для **DQS_MAIN** базы данных, а затем выберите **dqs_administrator**, **dqs_kb_editor** , или **dqs_kb_operator** флажок в **членство в роли для базы данных: DQS_MAIN** области, в зависимости от уровня доступа, необходимые пользователю.  
  
7.  В диалоговом окне **Создание имени входа** нажмите кнопку **ОК**, чтобы применить изменения.  
  
    > [!NOTE]  
    >  Если пользователю предоставляется роль **dqs_administrator** , примените изменения, а затем повторно проверьте разрешения пользователя; флажки двух других ролей DQS (**dq_kb_editor** и **dqs_kb_operator**) также должны быть установлены.  
  
  
