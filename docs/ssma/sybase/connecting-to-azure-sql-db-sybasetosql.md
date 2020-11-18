---
description: Подключение к базе данных SQL Azure (SybaseToSQL)
title: Подключение к базе данных SQL Azure (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/16/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9e77e4b0-40c0-455c-8431-ca5d43849aa7
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: f88b7b5357a61708910846f78c09f80e7c783957
ms.sourcegitcommit: 82b92f73ca32fc28e1948aab70f37f0efdb54e39
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94870426"
---
# <a name="connecting-to-azure-sql-database-sybasetosql"></a>Подключение к базе данных SQL Azure (SybaseToSQL)

Чтобы перенести базы данных Sybase в [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , необходимо подключиться к целевому экземпляру [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] . При подключении SSMA получает метаданные обо всех базах данных в экземпляре [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] и отображает метаданные базы данных в **обозревателе метаданных базы данных SQL Azure**. SSMA хранит сведения о экземпляре [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , к которому вы подключены, но не хранят пароли.

Подключение будет [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] оставаться активным до тех пор, пока проект не будет закрыт. При повторном открытии проекта необходимо повторно подключиться к, [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] Если требуется активное соединение с сервером. Вы можете работать в автономном режиме, пока объекты базы данных не будут загружены в [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] и не перенесены.

Метаданные экземпляра [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] не синхронизируются автоматически. Вместо этого для обновления метаданных в **обозревателе метаданных базы данных SQL Azure** необходимо вручную обновить [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] метаданные. Дополнительные сведения см. в подразделе «синхронизация метаданных базы данных SQL Azure» далее в этом разделе.

## <a name="required-azure-sql-database-permissions"></a>Необходимые разрешения базы данных SQL Azure

Для учетной записи, используемой для подключения к, [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] требуются другие разрешения в зависимости от действий, выполняемых учетной записью.

- Чтобы преобразовать объекты ASE в [!INCLUDE[tsql](../../includes/tsql-md.md)] синтаксис, обновить метаданные из [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] или сохранить преобразованный синтаксис в скрипты, учетная запись должна иметь разрешение на вход в экземпляр [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

- Чтобы загрузить объекты базы данных в [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , учетная запись должна быть членом роли базы данных **db_ddladmin** .

- Чтобы перенести данные в [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , учетная запись должна быть членом роли базы данных **db_owner** .

- Для запуска кода, созданного SSMA, учетная запись должна иметь `EXECUTE` разрешения для всех определяемых пользователем функций в схеме **ssma_syb** целевой базы данных. Эти функции предоставляют эквивалентные функции системных функций ASE и используются преобразованными объектами.

## <a name="establishing-an-azure-sql-database-connection"></a>Установка подключения к базе данных SQL Azure

Перед преобразованием объектов базы данных Sybase в [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] синтаксис необходимо установить соединение с экземпляром, на [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] котором требуется перенести базу данных или базы.

При определении свойств соединения также указывается база данных, в которую будут перенесены объекты и данные. Это сопоставление можно настроить на уровне схемы Sybase после подключения к базе данных SQL Azure. Дополнительные сведения см. [в разделе сопоставление схем ASE Sybase с SQL Server схемами &#40;&#41;SybaseToSQL ](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md).

> [!IMPORTANT]
> Прежде чем пытаться подключиться к [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , убедитесь, что IP-адрес разрешен через [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] брандмауэр.

Подключение к диспетчеру [!INCLUDE[ssAzure](../../includes/ssazure_md.md)]:

1. В меню **файл** выберите пункт **подключиться к базе данных SQL Azure**(этот параметр включен после создания проекта).
   Если ранее вы подключились к [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , имя команды будет **повторно подключено к базе данных SQL Azure**.

2. В диалоговом окне Соединение введите или выберите имя сервера [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

3. Введите, выберите или **Просмотрите** имя базы данных.

4. Введите или выберите **имя пользователя**.

5. Введите **пароль**.

6. SSMA рекомендует использовать зашифрованное соединение с [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

7. Нажмите кнопку **Соединить**.

## <a name="synchronizing-azure-sql-database-metadata"></a>Синхронизация метаданных базы данных SQL Azure

Метаданные о [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] базах данных не обновляются автоматически. Метаданные в обозревателе метаданных базы данных SQL Azure являются моментальными снимками метаданных при первом подключении к базе данных SQL Azure или при последнем обновлении метаданных вручную. Можно вручную обновить метаданные для всех баз данных или для любой отдельной базы данных или объекта базы данных. Для синхронизации метаданных:

1. Убедитесь, что вы подключены к [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

2. В **обозревателе метаданных базы данных SQL Azure** установите флажок рядом с базой данных или схемой базы данных, которую необходимо обновить.
   Например, чтобы обновить метаданные для всех баз данных, установите флажок рядом с пунктом **databases (базы данных**).

3. Щелкните правой кнопкой мыши **базы данных** или отдельную базу данных или схему базы данных, а затем выберите **синхронизировать с базой данных**.

## <a name="next-step"></a>Следующий шаг

Следующий шаг миграции зависит от потребностей проекта:

- Сведения о настройке сопоставления между схемами Sybase и [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] базами данных и схемами см. в статье [сопоставление схем ASE sybase с SQL Server схемами &#40;&#41;SybaseToSQL ](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md).
- Сведения о настройке параметров конфигурации для проектов см. в разделе [Установка параметров проекта &#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md).
- Сведения о настройке сопоставления исходных и целевых типов данных см. в разделе [Mapping SYBASE ASE and SQL Server Data types &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).
- Если не нужно выполнять какие – либо из этих задач, можно преобразовать определения объектов базы данных Sybase в [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] определения объектов. Дополнительные сведения см. в статье [Преобразование объектов базы данных SYBASE ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md).

## <a name="see-also"></a>См. также:

[Миграция баз данных Sybase ASE в SQL Server — база данных SQL Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)
