---
title: Подключение к базе данных SQL Azure (Акцесстоскл) | Документация Майкрософт
description: Узнайте, как подключиться к целевому экземпляру базы данных SQL Azure для миграции баз данных Access. SSMA получает метаданные о базах данных в базе данных SQL Azure.
ms.prod: sql
ms.custom: ''
ms.date: 11/16/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- instance of SQL Azure
- metadata, refreshing
- refreshing metadata
- SQL Azure
- SQL Azure, connecting
- SQL Azure, connecting to
- SQL Azure, reconnecting
- SQL Azure, synchronizing metadata
ms.assetid: 1ba0d113-dc05-4431-8689-e14a8821bafd
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: f910e9c07bf4318419714b97e4f4db742c913753
ms.sourcegitcommit: 82b92f73ca32fc28e1948aab70f37f0efdb54e39
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94869472"
---
# <a name="connecting-to-azure-sql-database-accesstosql"></a>Подключение к базе данных SQL Azure (Акцесстоскл)

Чтобы перенести базы данных Access в [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , необходимо подключиться к целевому экземпляру [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] . При подключении SSMA получает метаданные обо всех базах данных в экземпляре [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] и отображает метаданные базы данных в **обозревателе метаданных базы данных SQL Azure**. SSMA хранит сведения о том, к какому экземпляру [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] вы подключены, но не хранят пароли.

Подключение будет [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] оставаться активным до тех пор, пока проект не будет закрыт. При повторном открытии проекта необходимо повторно подключиться к, [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] Если требуется активное соединение с сервером. Вы можете работать в автономном режиме, пока объекты базы данных не будут загружены в [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] и не перенесены.

Метаданные экземпляра [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] не синхронизируются автоматически. Вместо этого для обновления метаданных в **обозревателе метаданных базы данных SQL Azure** необходимо вручную обновить [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] метаданные. Дополнительные сведения см. в подразделе «синхронизация метаданных базы данных SQL Azure» далее в этом разделе.

## <a name="required-azure-sql-database-permissions"></a>Необходимые разрешения базы данных SQL Azure

Для учетной записи, используемой для подключения к, [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] требуются другие разрешения в зависимости от действий, выполняемых учетной записью.

- Чтобы преобразовать объекты доступа в [!INCLUDE[tsql](../../includes/tsql-md.md)] синтаксис, обновить метаданные из [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] или сохранить преобразованный синтаксис в скрипты, учетная запись должна иметь разрешение на вход в экземпляр [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

- Чтобы загрузить объекты базы данных в [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , учетная запись должна быть членом роли базы данных **db_ddladmin** .

- Чтобы перенести данные в [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , учетная запись должна быть членом роли базы данных **db_owner** .

## <a name="establishing-an-azure-sql-database-connection"></a>Установка подключения к базе данных SQL Azure

Перед преобразованием объектов базы данных Access в [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] синтаксис необходимо установить соединение с экземпляром, на [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] котором требуется перенести базу данных или базы.

При определении свойств соединения также указывается база данных, в которую будут перенесены объекты и данные. Это сопоставление можно настроить на уровне схемы доступа после подключения к [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] . Дополнительные сведения см. [в разделе Сопоставление баз данных Access с SQL Server схемами](mapping-source-and-target-databases-accesstosql.md).
  
> [!IMPORTANT]
> Прежде чем пытаться подключиться к [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , убедитесь, что IP-адрес разрешен через [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] брандмауэр.
  
Подключение к диспетчеру [!INCLUDE[ssAzure](../../includes/ssazure_md.md)]:

1. В меню **файл** выберите команду **подключиться к SQL Azure** (этот параметр включен после создания проекта).
   Если ранее вы подключились к [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , имя команды будет **повторно подключено к SQL Azure**.

2. В диалоговом окне Соединение введите или выберите имя сервера [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

3. Введите, выберите или **Просмотрите** имя базы данных.

4. Введите или выберите **имя пользователя**.

5. Введите **пароль**.

6. SSMA рекомендует использовать зашифрованное соединение с [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

7. Нажмите кнопку **Соединить**.
  
Если в службах нет баз данных [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , можно создать первую базу данных с помощью параметра **создать базу данных Azure** , который отображается при нажатии кнопки **Обзор** .

## <a name="synchronizing-azure-sql-database-metadata"></a>Синхронизация метаданных базы данных SQL Azure

Метаданные о базах данных в не [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] обновляются автоматически. Метаданные в **обозревателе метаданных базы данных SQL Azure** являются моментальными снимками метаданных при первом подключении к [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] или при последнем обновлении метаданных вручную. Можно вручную обновить метаданные для всех баз данных или для любой отдельной базы данных или объекта базы данных. Для синхронизации метаданных:

1. Убедитесь, что вы подключены к [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

2. В **обозревателе метаданных базы данных SQL Azure** установите флажок рядом с базой данных или схемой базы данных, которую необходимо обновить.
   Например, чтобы обновить метаданные для всех баз данных, установите флажок рядом с пунктом **databases (базы данных**).

3. Щелкните правой кнопкой мыши **базы данных** или отдельную базу данных или схему базы данных, а затем выберите **синхронизировать с базой данных**.

## <a name="refreshing-azure-sql-database-metadata"></a>Обновление метаданных базы данных SQL Azure

Если [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] схемы изменяются после подключения, можно обновить метаданные с сервера.

Обновление [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] метаданных:

- В **обозревателе метаданных базы данных SQL Azure** щелкните правой кнопкой мыши узел **базы данных** и выберите команду **Обновить из базы данных**.

## <a name="reconnecting-to-azure-sql-database"></a>Повторное подключение к базе данных SQL Azure

Подключение будет [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] оставаться активным до тех пор, пока проект не будет закрыт. При повторном открытии проекта необходимо повторно подключиться к, [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] Если требуется активное соединение с сервером. Вы можете работать в автономном режиме, пока объекты базы данных не будут загружены в [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] и не перенесены.

Процедура повторного подключения к совпадает с [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] процедурой установки соединения.

## <a name="next-steps"></a>Следующие шаги

Следующий шаг миграции зависит от потребностей проекта:

- Сведения о настройке сопоставления между схемами доступа и базой данных SQL Azure см. в разделе [Сопоставление баз данных Access с SQL Server схемами](mapping-source-and-target-databases-accesstosql.md).
- Сведения о настройке параметров конфигурации для проектов см. в разделе [Задание параметров проекта](setting-conversion-and-migration-options-accesstosql.md).
- Сведения о настройке сопоставления исходного и целевого типов данных см. в разделе [Сопоставление исходных и целевых типов данных](mapping-source-and-target-data-types-accesstosql.md).
- Если не нужно выполнять какие – либо из этих задач, можно преобразовать определения объектов базы данных Access в SQL Azure определения объектов. Дополнительные сведения см. в разделе [Преобразование баз данных Access](converting-access-database-objects-accesstosql.md).

## <a name="see-also"></a>См. также:

[Миграция баз данных Access в SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)
