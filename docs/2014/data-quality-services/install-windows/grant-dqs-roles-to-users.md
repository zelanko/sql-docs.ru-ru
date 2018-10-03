---
title: Предоставление ролей DQS пользователям | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: afb445b5-bdbe-4bfe-844f-344766cdc2b2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 250d45bd6acf2165f922e311931fd5a13f633d9e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218994"
---
# <a name="grant-dqs-roles-to-users"></a>Предоставление ролей DQS пользователям
  В этом разделе описывается создание имен входа SQL Server на основе участников Windows и предоставление им ролей служб [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) в базе данных DQS_MAIN.  
  
## <a name="prerequisites"></a>предварительные требования  
  
-   Необходимо, чтобы установка сервера [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] , запускаемая с помощью файла DQSInstaller.exe, была завершена. Дополнительные сведения см. в разделе [Запуск файла DQSInstaller.exe для завершения установки сервера служб DQS](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
-   Учетная запись пользователя Windows должна входить в соответствующую предопределенную роль сервера (например, securityadmin, serveradmin или sysadmin) для создания имен входа SQL Server и предоставления им ролей DQS.  
  
### <a name="to-create-sql-login-and-grant-dqs-roles"></a>Создание имени входа SQL Server и предоставление ролей DQS  
  
1.  Запустите среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
2.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]разверните экземпляр SQL Server, а затем узел **Безопасность**.  
  
3.  Щелкните папку **Безопасность** правой кнопкой мыши, наведите указатель на пункт **Создать**и выберите пункт **Имя входа**.  
  
4.  В диалоговом окне **Создание имени входа** укажите имя пользователя Windows в поле **Имя входа** , выберите для типа проверки подлинности **Проверка подлинности Windows**и нажмите кнопку **Поиск** для проверки пользователя.  
  
5.  После проверки пользователя щелкните страницу **Сопоставление пользователей** в левой части окна.  
  
6.  В правой области установите флажок в столбце **Сопоставление** для базы данных **DQS_MAIN** , а затем на панели **Членство в роли базы данных для: DQS_MAIN**установите флажок **dqs_administrator**, **dqs_kb_editor** или **dqs_kb_operator** в зависимости от уровня доступа, который требуется пользователю. Дополнительные сведения о трех ролях служб DQS см. в разделе [DQS Security](../dqs-security.md).  
  
7.  В диалоговом окне **Создание имени входа** нажмите кнопку **ОК** , чтобы применить изменения.  
  
    > [!NOTE]  
    >  Если пользователю предоставляется роль **dqs_administrator** , примените изменения, а затем повторно проверьте разрешения пользователя; флажки двух других ролей DQS (**dq_kb_editor** и **dqs_kb_operator**) также должны быть установлены.  
  
## <a name="next-steps"></a>Следующие шаги  
 Выполните вход на сервер [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] с использованием учетной записи пользователя Windows, для которой только что было создано имя входа SQL Server и предоставлена роль DQS.  
  
## <a name="see-also"></a>См. также  
 [Установка служб Data Quality Services](install-data-quality-services.md)   
 [Создание имени для входа](../../relational-databases/security/authentication-access/create-a-login.md)  
  
  
