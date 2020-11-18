---
description: Подключение к базе данных SQL Azure (MySQLToSQL)
title: Подключение к базе данных SQL Azure (MySQLToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 11/16/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Connecting to Azure SQL Database, SQL Azure permissions
- Connecting to Azure SQL Database, synchronization
ms.assetid: d0b6f16a-1880-459d-a0c7-28b7ef15c56a
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 6604d35058c9e8876638beee3ec6d73a9cd7a491
ms.sourcegitcommit: 82b92f73ca32fc28e1948aab70f37f0efdb54e39
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94870097"
---
# <a name="connecting-to-azure-sql-database-mysqltosql"></a>Подключение к базе данных SQL Azure (MySQLToSQL)

Чтобы перенести базы данных MySQL в [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , необходимо подключиться к целевому экземпляру [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] . При подключении SSMA получает метаданные обо всех базах данных в экземпляре [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] и отображает метаданные базы данных в **обозревателе метаданных базы данных SQL Azure**. SSMA хранит сведения о экземпляре [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , к которому вы подключены, но не хранят пароли.

Подключение будет [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] оставаться активным до тех пор, пока проект не будет закрыт. При повторном открытии проекта необходимо повторно подключиться к, [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] Если требуется активное соединение с сервером. Вы можете работать в автономном режиме, пока объекты базы данных не будут загружены в [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] и не перенесены.

Метаданные экземпляра [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] не синхронизируются автоматически. Вместо этого для обновления метаданных в **обозревателе метаданных базы данных SQL Azure** необходимо вручную обновить [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] метаданные. Дополнительные сведения см. в подразделе «синхронизация метаданных базы данных SQL Azure» далее в этом разделе.

## <a name="required-azure-sql-database-permissions"></a>Необходимые разрешения базы данных SQL Azure

Для учетной записи, используемой для подключения к, [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] требуются другие разрешения в зависимости от действий, выполняемых учетной записью.

- Чтобы преобразовать объекты MySQL в [!INCLUDE[tsql](../../includes/tsql-md.md)] синтаксис, обновить метаданные из [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] или сохранить преобразованный синтаксис в скрипты, учетная запись должна иметь разрешение на вход в экземпляр [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

- Чтобы загрузить объекты базы данных в [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , учетная запись должна быть членом роли базы данных **db_ddladmin** .

- Чтобы перенести данные в [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , учетная запись должна быть членом роли базы данных **db_owner** .

## <a name="establishing-an-azure-sql-database-connection"></a>Установка подключения к базе данных SQL Azure

Перед преобразованием объектов базы данных MySQL в [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] синтаксис необходимо установить соединение с экземпляром, на [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] котором требуется перенести базу данных или базы MySQL.

При определении свойств соединения также указывается база данных, в которую будут перенесены объекты и данные. Это сопоставление можно настроить на уровне схемы MySQL после подключения к [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] . Дополнительные сведения см. [в разделе Сопоставление баз данных MySQL с SQL Server схемами &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md).

> [!IMPORTANT]
> Прежде чем пытаться подключиться к [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , убедитесь, что IP-адрес разрешен через [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] брандмауэр.

Подключение к диспетчеру [!INCLUDE[ssAzure](../../includes/ssazure_md.md)]:

1. В меню **файл** выберите пункт **подключиться к базе данных SQL Azure** (этот параметр включен после создания проекта).
   Если ранее вы подключились к [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , имя команды будет **повторно подключено к базе данных SQL Azure**.

2. В диалоговом окне Соединение введите или выберите имя сервера [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

3. Введите, выберите или **Просмотрите** имя базы данных.

4. Введите или выберите **имя пользователя**.

5. Введите **пароль**.

6. SSMA рекомендует использовать зашифрованное соединение с [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

7. Нажмите кнопку **Соединить**.
  
## <a name="synchronizing-azure-sql-database-metadata"></a>Синхронизация метаданных базы данных SQL Azure

Метаданные о базах данных в не [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] обновляются автоматически. Метаданные в **обозревателе метаданных базы данных SQL Azure** являются моментальными снимками метаданных при первом подключении к [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] или при последнем обновлении метаданных вручную. Можно вручную обновить метаданные для всех баз данных или для любой отдельной базы данных или объекта базы данных. Для синхронизации метаданных:

1. Убедитесь, что вы подключены к [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

2. В **обозревателе метаданных базы данных SQL Azure** установите флажок рядом с базой данных или схемой базы данных, которую необходимо обновить.
   Например, чтобы обновить метаданные для всех баз данных, установите флажок рядом с пунктом **databases (базы данных**).

3. Щелкните правой кнопкой мыши **базы данных** или отдельную базу данных или схему базы данных, а затем выберите **синхронизировать с базой данных**.

## <a name="next-step"></a>Следующий шаг

Следующий шаг миграции зависит от потребностей проекта:

- Чтобы настроить сопоставление между схемами MySQL и [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , см. раздел [Сопоставление баз данных mysql с SQL Server схемами &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md).
- Сведения о настройке параметров конфигурации для проектов см. в разделе [Установка параметров проекта &#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md).
- Сведения о настройке сопоставления исходных и целевых типов данных см. в разделе [Сопоставление типов данных MySQL и SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md).
- Если не нужно выполнять какие – либо из этих задач, можно преобразовать определения объектов базы данных MySQL в [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] определения объектов. Дополнительные сведения см. в статье [Преобразование баз данных MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md).

## <a name="see-also"></a>См. также:

[Перенос баз данных MySQL в SQL Server базы данных SQL Azure &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)
