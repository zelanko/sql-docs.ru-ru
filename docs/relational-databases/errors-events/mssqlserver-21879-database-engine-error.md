---
title: "MSSQLSERVER_21879 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 21879 (Database Engine error)
ms.assetid: fcfab735-05ca-423a-89f1-fdee7e2ed8c0
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3d366b7cc857471370afd18b28b8ee9c9b3e561a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver21879"></a>MSSQLSERVER_21879
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21879|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLErrorNum21879|  
|Текст сообщения|Не удалось выполнить запрос к перенаправленному серверу «%s» исходного издателя «%s» и базы данных издателя «%s», чтобы определить имя удаленного сервера. Ошибка %d, сообщение об ошибке «%s».|  
  
## <a name="explanation"></a>Объяснение  
**sp_validate_redirected_publisher** использует временно связанный сервер, создаваемый для подключения к перенаправленному издателю, чтобы обнаружить имя удаленного сервера. Ошибка 21879 возвращается при неудачном выполнении запроса к связанному серверу. Вызов для запроса имени удаленного сервера обычно является первым обращением ко временно связанному серверу, поэтому при наличии проблем с соединением они, скорее всего, проявятся при этом вызове. Этот удаленный вызов просто выполняет select **@@servername** на удаленном сервере.  
  
Связанный сервер, используемый для выполнения запроса перенаправляемого издателя, применяет режим безопасности, имя входа и пароль, заданные при вызове хранимой процедуры **sp_adddistpublisher** для исходного издателя.  
  
-   Если использовалась проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (режим безопасности 0), то для подключения к удаленному серверу используются указанные имя пользователя и пароль.  
  
-   Если используется проверка подлинности Windows (режим безопасности 1), то для соединения используется доверительное соединение.  
  
    -   Если хранимая процедура **sp_validate_redirected_publisher** явно вызывается пользователем, то для соединения используется имя входа Windows, с помощью которого пользователь вошел в систему.  
  
    -   Если издатель хранимой процедуры **sp_validate_redirected_** вызывается агентом репликации из **sp_get_redirected_publisher**, то используется связанное с агентом имя входа Windows.  
  
Ошибка 21879 может указывать, что хранимая процедура **sp_validate_redirected_publisher** была вызвана с именем входа, неизвестным на перенаправленном целевом издателе.  
  
## <a name="user-action"></a>Действие пользователя  
Убедитесь, что имя входа, используемое для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], или имя входа проверки подлинности Windows действительно на всех репликах группы доступности и имеет авторизацию для доступа к таблицам метаданных подписок (syssubscriptions и sysmergesubscriptions) в базе данных издателя.  
  
Необходимо учитывать следующее, если ошибка 21879 возвращается из вызова хранимой процедуры **sp_get_redirected_publisher**, инициированного агентом репликации, который выполняется на отличном от распространителя узле, например когда агент слияния выполняется на подписчике. Если для соединения с перенаправленным издателем используется проверка подлинности Windows, то для успешной установки соединения необходимо настроить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для проверки подлинности Kerberos. Когда используется проверка подлинности Windows, а [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не настроен для проверки подлинности Kerberos, выполняющийся на подписчике агент слияния получает ошибку 18456, указывающую на невозможность выполнения входа от имени «NT AUTHORITY\ANONYMOUS LOGON». Существует три способа решения этой проблемы:  
  
-   Настройка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для проверки подлинности Kerberos. Ознакомьтесь со статьей **Kerberos Authentication and SQL Server** (Проверка подлинности Kerberos и SQL Server) в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Используйте хранимую процедуру **sp_changedistpublisher** для изменения режима безопасности, связанного с исходным издателем в MSdistpublishers, а также для указания имени входа и пароля, используемых при соединении.  
  
-   Укажите параметр командной строки *BypassPublisherValidation* в командной строке агента слияния, чтобы пропустить проверку при запуске **sp_get_redirected_publisher** на распространителе.  
  
