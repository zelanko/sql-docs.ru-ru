---
title: Роли приложений | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- application roles [SQL Server], about application roles
- principals [SQL Server], application roles
- credentials [SQL Server], roles
- application roles [SQL Server]
- roles [SQL Server], application
- permissions [SQL Server], roles
- users [SQL Server], application roles
- authentication [SQL Server], roles
- groups [SQL Server], roles
ms.assetid: dca18b8a-ca03-4b7f-9a46-8474d5b66f76
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: b82ecbd1fffd99e5830948f0bf2bb799d6f1a851
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43019903"
---
# <a name="application-roles"></a>Роли приложений
  Роль приложения — это участник базы данных, позволяющий приложению выполняться со своими, подобными пользовательским, правами доступа. Роли приложений можно использовать для разрешения доступа к определенным данным только тем пользователям, которые подключены посредством конкретного приложения. В отличие от ролей баз данных, роли приложений не содержат элементов и по умолчанию находятся в неактивном состоянии. Роли приложений работают с обоими режимами проверки подлинности. Роли приложений активируются с помощью процедуры **sp_setapprole**, которая требует указания пароля. Так как роли приложений являются участниками на уровне базы данных, они имеют доступ к другим базам данных только с разрешениями, предоставленными учетной записи пользователя **guest**в этих базах данных. Таким образом, любая база данных, в которой была отключена учетная запись пользователя **guest** , не будет доступна для ролей приложений в других базах данных.  
  
 В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]роли приложений не имеют доступ к метаданным уровня сервера, так как они не связаны с участником на уровне сервера. Чтобы отключить это ограничение, позволив тем самым ролям приложений получать доступ к метаданным уровня сервера, установите глобальный флаг 4616. Дополнительные сведения см. в разделах [Флаги трассировки (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql) и [DBCC TRACEON (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-traceon-transact-sql).  
  
## <a name="connecting-with-an-application-role"></a>Соединение с ролью приложения  
 Ниже представлены этапы процесса, при помощи которого роль приложения переключает контексты безопасности.  
  
1.  Пользователь выполняет клиентское приложение.  
  
2.  Клиентское приложение соединяется с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в качестве пользователя.  
  
3.  Приложение выполняет хранимую процедуру **sp_setapprole** с использованием пароля, известного только этому приложению.  
  
4.  Если имя и пароль роли приложения достоверны, она становится активной.  
  
5.  На этом этапе соединение утрачивает разрешения пользователя и приобретает разрешения роли приложения.  
  
 Разрешения, полученные через роль приложения, действуют в течение всего соединения.  
  
 В более ранних версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]единственным способом для пользователя вновь приобрести свой исходный контекст безопасности после активации роли приложения было отсоединение и повторное соединение с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Начиная с версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]процедура **sp_setapprole** имеет новый параметр, который создает файл cookie. Этот файл содержит сведения о контексте до того, как роль приложения переходит в активное состояние. Файл cookie может использоваться процедурой **sp_unsetapprole** для возврата сеанса в исходный контекст. Сведения об этом новом параметре и пример см. в разделе [sp_setapprole (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-setapprole-transact-sql)в этих базах данных.  
  
> [!IMPORTANT]  
>  Параметр **encrypt** ODBC не поддерживается в **SqlClient**. При передаче конфиденциальных сведений по сети следует пользоваться протоколом SSL или IPSec для шифрования канала. Если необходимо сохранить учетные данные в клиентском приложении, следует зашифровать их при помощи функций API шифрования. В [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях параметр *password* хранится в виде одностороннего хэша.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|||  
|-|-|  
|Создание роли приложения.|[Создание роли приложения](create-an-application-role.md) и [CREATE APPLICATION ROLE (Transact-SQL)](/sql/t-sql/statements/create-application-role-transact-sql)|  
|Изменение роли приложения.|[ALTER APPLICATION ROLE (Transact-SQL)](/sql/t-sql/statements/alter-application-role-transact-sql)|  
|Удаление роли приложения.|[DROP APPLICATION ROLE (Transact-SQL)](/sql/t-sql/statements/drop-application-role-transact-sql)|  
|Использование роли приложения.|[sp_setapprole (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-setapprole-transact-sql)|  
  
## <a name="see-also"></a>См. также  
 [Обеспечение безопасности SQL Server](../securing-sql-server.md)  
  
  
