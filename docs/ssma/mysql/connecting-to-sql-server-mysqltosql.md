---
title: Подключение к SQL Server (MySQLToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- connecting to SQL Server 2008, SQL Server permission
- connecting to SQL Server 2008, synchronization
ms.assetid: 08233267-693e-46e6-9ca3-3a3dfd3d2be7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 64dd3fae9776c09f81571a721aa53753e34fbb17
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52412291"
---
# <a name="connecting-to-sql-server-mysqltosql"></a>Подключение к SQL Server (MySQLToSQL)
Чтобы перенести базы данных MySQL в SQL Server, необходимо подключиться к целевому экземпляру SQL Server. При подключении, SSMA получает метаданные обо всех базах данных в экземпляре SQL Server и отображает метаданные базы данных в обозревателе метаданных SQL Server. SSMA хранят сведения о экземпляра SQL Server, вы подключены, но не хранит пароли.  
  
Подключение к SQL Server остается активным, пока не закрыть проект. При повторном открытии проекта, вы должны повторно подключиться к SQL Server если требуется активное подключение к серверу. Вы можете работать вне сети до загрузки объектов базы данных в SQL Server и перенос данных.  
  
Метаданные об экземпляре SQL Server автоматически не синхронизирован. Вместо этого для обновления метаданных в обозревателе метаданных SQL Server, необходимо вручную обновить метаданные SQL Server. Дополнительные сведения см. в разделе «Синхронизация метаданных SQL Server» далее в этом разделе.  
  
## <a name="required-sql-server-permissions"></a>Разрешения требуется SQL Server  
Учетная запись, которая используется для подключения к SQL Server требует разных разрешений в зависимости от действий, выполняемых в учетной записи:  
  
-   Для преобразования объектов MySQL для [!INCLUDE[tsql](../../includes/tsql-md.md)] синтаксис, для обновления метаданных из SQL Server, или сохранить преобразованный синтаксис для сценариев, учетная запись должна иметь разрешение на вход в экземпляр SQL Server.  
  
-   Чтобы загрузить объекты базы данных в SQL Server, требование минимально необходимым разрешением является членство в **db_owner** роли базы данных в целевую базу данных.  
  
## <a name="establishing-a-sql-server-connection"></a>Установки подключения к серверу SQL  
Перед началом преобразования объектов базы данных MySQL в синтаксис SQL Server, необходимо установить подключение к экземпляру SQL Server, где необходимо выполнить миграцию базы данных MySQL или баз данных.  
  
При определении свойств соединения, также указать базу данных, где объекты и данные будут перенесены. Это сопоставление на уровне схемы MySQL можно настроить, после подключения к SQL Server. Дополнительные сведения см. в разделе [сопоставление баз данных MySQL со схемами SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
> [!IMPORTANT]  
> Прежде чем попытаться подключиться к SQL Server, убедитесь, что экземпляр SQL Server запущен и может принимать подключения.  
  
**Для подключения к SQL Server**  
  
1.  На **файл** меню, выберите **подключение к SQL Server** (этот параметр включен после создания проекта).  
  
    Если вы ранее подключались к SQL Server, команда будет называться **повторно подключиться к SQL Server**.  
  
2.  В диалоговом окне подключения введите или выберите имя экземпляра SQL Server.  
  
    -   Если вы подключаетесь к экземпляру по умолчанию на локальном компьютере, можно ввести **localhost** или точку (**.**).  
  
    -   Если вы подключаетесь к экземпляру по умолчанию на другом компьютере, введите имя компьютера.  
  
    -   Если вы подключаетесь к именованному экземпляру на другом компьютере, введите имя компьютера, следуют обратную косую черту и имя экземпляра, например Сервер\экземпляр.  
  
3.  Если экземпляр SQL Server настроен на прием подключений через нестандартный порт, введите номер порта, который используется для подключения к SQL Server в **порт сервера** поле. Для экземпляра SQL Server по умолчанию номер порта по умолчанию — 1433. Для именованных экземпляров SSMA будет пытаться получить номер порта от службы обозревателя SQL Server.  
  
4.  В **проверки подлинности** выберите тип проверки подлинности, используемый для соединения. Чтобы использовать текущую учетную запись Windows, выберите **проверки подлинности Windows**. Чтобы использовать имя входа SQL Server, выберите проверку подлинности SQL Server и укажите имя для входа и пароль.  
  
5.  Для безопасного подключения, добавляются два элемента управления, **шифровать соединение** и **TrustServerCertificate** флажки. Только тогда, когда **шифровать соединение** установлен, **TrustServerCertificate** флажок становится видимым. Когда **шифровать соединение** проверяется (true) и **TrustServerCertificate** снят (false), он будет проверять сертификат SSL сервера SQL. Проверка сертификата сервера является частью SSL-подтверждения и гарантирует, что для подключения выбран правильный сервер. Чтобы обеспечить это, необходимо установить сертификат на стороне клиента, а также на стороне сервера.  
  
6.  Нажмите кнопку "Подключить".  
  
**Выше совместимость версий**  
  
Он может подключаться или повторно подключиться к более поздним версиям SQL Server.  
  
1.  Вы сможете подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, если проект создан не [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005.  
  
2.  Вы сможете подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, если проект создан не [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008, но он не допускается для подключения к более ранние версии, т. е. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005.  
  
3.  Вы сможете подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, если проект создан не [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012.  
  
4.  Можно подключиться только к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, если проект создан не [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014.  
  
5.  Выше совместимость версий не является допустимым для «SQL Azure».  
  
||||||||  
|-|-|-|-|-|-|-|  
|**ВЕРСИЯ целевого сервера Vs тип проекта**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005<br /> (Версия: 9.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008<br /> (Версия: 10.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012<br />(Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014<br />(Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016<br />(Version:13.x)|SQL Azure|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005|Да|Да|Да|Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008||Да|Да|Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|||Да|Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014||||Да|Да||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2016|||||Да||  
|SQL Azure||||||Да|  
  
> [!IMPORTANT]  
> Преобразование объектов базы данных выполняется в соответствии с типом проекта, но не в соответствии с версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подключен. Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 проекта преобразования выполняется согласно [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] несмотря на то, что вы подключены к более поздней версии 2005 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQL Server 2008 или SQL Server 2012 или SQL Server 2014 или SQL Server 2016).  
  
## <a name="synchronizing-sql-server-metadata"></a>Синхронизация метаданных SQL Server  
Метаданные о базах данных SQL Server не обновляется автоматически. Метаданные в обозревателе метаданных SQL Server — моментальный снимок метаданные при при первом подключении к SQL Server или последнего времени, когда вручную обновленных метаданных. Можно вручную обновить метаданные для всех баз данных или для любой отдельной базы данных или объект базы данных.  
  
**Чтобы синхронизировать метаданные**  
  
1.  Убедитесь, что вы подключены к SQL Server.  
  
2.  В обозревателе метаданных SQL Server установите флажок рядом с именем базы данных или схему базы данных, который требуется обновить.  
  
    К примеру чтобы обновить метаданные для всех баз данных, выберите флажок рядом с базами данных.  
  
3.  Щелкните правой кнопкой мыши баз данных, или отдельной базы данных или схему базы данных, а затем выберите **синхронизация с базой данных**.  
  
## <a name="next-step"></a>Следующий шаг  
Следующий шаг в процессе переноса зависит от требований проекта:  
  
-   Чтобы настроить сопоставление между схемы MySQL и баз данных SQL Server и схемы, см. в разделе [сопоставление баз данных MySQL со схемами SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
-   Чтобы настроить параметры конфигурации для проектов, см. в разделе [Настройка параметров проекта &#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md)  
  
-   Чтобы настроить сопоставление исходной и целевой типы данных, см. в разделе [сопоставление MySQL и типы данных SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
-   Если у вас нет для выполнения этих задач, можно преобразовать определения объектов базы данных MySQL в определения объектов SQL Server. Дополнительные сведения см. в разделе [преобразование баз данных MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>См. также  
[Миграция MySQL базы данных в SQL Server — база данных Azure SQL &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
