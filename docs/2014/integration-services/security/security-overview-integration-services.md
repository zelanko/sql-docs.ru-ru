---
title: Общие сведения о безопасности (службы Integration Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, security
- Integration Services, security
- security [Integration Services], about security
- passwords [Integration Services]
- packages [Integration Services], security
- SQL Server Integration Services, security
- SSIS, security
- Integration Services packages, security
- SQL Server Integration Services packages, security
ms.assetid: 01aa0b88-d477-4581-9a3b-2efc3de2b133
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b2e86fff86e24668e7fe6382545e024bed1a4025
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62927104"
---
# <a name="security-overview-integration-services"></a>Общие сведения о безопасности (службы Integration Services)
  Безопасность служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] обеспечивается несколькими уровнями защиты, которые составляют насыщенную и гибкую среду безопасности. Эти уровни безопасности включают в себя использование цифровых подписей, свойств уровня пакетов, ролей базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и разрешений операционной системы. Большинство этих функций безопасности относятся к категории управления доступом и удостоверениями.  
  
## <a name="identity-features"></a>Функции управления удостоверениями  
 Применение функций управления удостоверениями в пакетах позволяет достичь следующей цели.  
  
 **Обеспечение открытия и запуск только пакетов из надежных источников**  
  
 Чтобы гарантировать открытие и выполнение только пакетов из надежных источников, необходимо сначала определить источник пакетов. Определить источник можно, подписывая пакеты с использованием сертификатов. Затем при открытии или запуске пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] может проверить наличие и правильность цифровой подписи. Дополнительные сведения см. в разделе [Определение источника пакетов с помощью цифровых подписей](identify-the-source-of-packages-with-digital-signatures.md).  
  
## <a name="access-control-features"></a>Функции управления доступом  
 Применение функций управления удостоверениями в пакетах позволяет достичь следующей цели.  
  
 **Обеспечение открытия и запуск пакетов только зарегистрированными пользователями**  
  
 Чтобы обеспечить открытие и запуск пакетов только зарегистрированными пользователями, необходимо управлять доступом к следующим данным.  
  
-   Управлять доступом к содержимому пакетов, особенно конфиденциальным данным.  
  
-   Управлять доступом к пакетам и конфигурациям пакетов, хранимым в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Управлять доступом к пакетам и связанным файлам, таким как файлы конфигурации, журналов и контрольных точек, хранимым в файловой системе.  
  
-   Управлять доступом к службе [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и сведениям о пакетах, отображаемых службой в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
### <a name="controlling-access-to-the-contents-of-packages"></a>Управление доступом к содержимому пакетов  
 Чтобы помочь ограничить доступ к содержимому пакета, можно зашифровать пакеты, устанавливая свойство ProtectionLevel пакета. Это свойство можно установить на уровень защиты, необходимый пакету. Например, в среде групповой разработки пакет может быть зашифрован при помощи пароля, который известен членам группы, принимающим участие в его разработке.  
  
 При установке свойства ProtectionLevel пакета службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] автоматически определяют конфиденциальные свойства и обрабатывают их согласно определенному уровню защиты пакетов. Например, свойство ProtectionLevel пакета установлено на уровень, на котором конфиденциальные сведения шифруются с паролем. Для этого пакета службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] автоматически шифруют значения всех конфиденциальных свойств и не отображают соответствующие данные, если не указан верный пароль.  
  
 Обычно службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] определяют свойства как конфиденциальные, если эти свойства содержат такие сведения, как пароль или строка соединения, или если эти свойства соответствуют переменным или сформированным задачей XML-узлам. В службах [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] свойство рассматривается как конфиденциальное в зависимости от того, назначил ли свойство конфиденциальным разработчик компонента [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , такого как диспетчер соединений или задача. Пользователи не могут добавлять или удалять свойства из списка свойств, считающихся конфиденциальными. Разработчики пользовательских задач, диспетчеров соединений или компонентов потоков данных могут указать свойства, которые службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] рассматривают как конфиденциальные.  
  
 Дополнительные сведения см. в разделе [Access Control for Sensitive Data in Packages](access-control-for-sensitive-data-in-packages.md).  
  
### <a name="controlling-access-to-packages"></a>Управление доступом к пакетам  
 Пакеты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] могут быть сохранены в базе данных msdb экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]или в файловой системе как XML-файлы с расширением DTSX. Дополнительные сведения см. в разделе [Сохранение пакетов](../save-packages.md).  
  
#### <a name="saving-packages-to-the-msdb-database"></a>Сохранение пакетов в базе данных msdb  
 Сохранение пакетов в базе данных msdb способствует повышению безопасности на уровне сервера, базы данных и таблиц. В базе данных msdb пакеты [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] хранятся в таблице sysssispackages. Поскольку пакеты хранятся в таблицах sysssispackages и sysdtspackages в базе данных msdb, резервное копирование пакетов выполняется автоматически при резервном копировании базы данных msdb.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пакеты, хранящиеся в базе данных msdb, также можно защитить, применив роли уровня базы данных [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] содержат три предопределенные роли базы данных, предназначенные для управления доступом к пакетам: db_ssisadmin, db_ssisltduser и db_ssisoperator. Роль с правом чтения и правом записи может быть определена для каждого пакета. Для использования в пакетах служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] можно также определить пользовательские роли уровня базы данных. Роли могут быть реализованы только в пакетах, которые хранятся в базе данных msdb экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Роли служб Integration Services (службы SSIS)](integration-services-roles-ssis-service.md).  
  
#### <a name="saving-packages-to-the-file-system"></a>Сохранение пакетов в файловой системе  
 Если пакеты хранится в файловой системе вместо базы данных msdb, убедитесь в безопасности файлов пакетов и папок, содержащих файлы пакетов.  
  
### <a name="controlling-access-to-files-used-by-packages"></a>Управление доступом к файлам, используемым пакетами  
 Пакеты, настроенные для использования конфигураций, контрольных точек и журналов, создают данные, которые хранятся вне пакетов. Эти данные могут быть конфиденциальными и должны быть защищены. Файлы контрольных точек могут быть сохранены только в файловой системе, а конфигурации и протоколы — либо в файловой системе, либо в таблицах базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Сохраненные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] конфигурации и протоколы защищены системой безопасности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , но данные, записанные в файловую систему, требуют дополнительной защиты.  
  
 Дополнительные сведения см. в разделе [Доступ к файлам, используемым пакетами](../access-to-files-used-by-packages.md).  
  
#### <a name="storing-package-configurations-securely"></a>Безопасное сохранение конфигураций пакетов  
 Конфигурации пакетов могут быть сохранены в таблице базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или в файловой системе.  
  
 Конфигурации могут быть сохранены в любой базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а не только в базе данных msdb. Таким образом, можно указать базу данных, которая используется в качестве репозитория для конфигураций пакетов. Также можно задать название таблицы, которая будет хранить конфигурацию, и службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] автоматически создадут таблицу с правильной структурой. Сохранение конфигурации в таблице позволяет обеспечить безопасность на уровне сервера, базы данных и таблиц. Кроме того, происходит автоматическое резервное копирование конфигурации, сохраненной в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , при создании резервной копии базы данных.  
  
 Если конфигурация хранится в файловой системе вместо базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], убедитесь в безопасности папок, содержащих файлы конфигурации пакетов.  
  
 Дополнительные сведения о конфигурациях см. в разделе [Package Configurations](../package-configurations.md).  
  
### <a name="controlling-access-to-the-integration-services-service"></a>Управление доступом к службе Integration Services  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] использует службу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Чтобы запретить неавторизованным пользователям просмотр сведений о пакетах, сохраненных на локальных и удаленных компьютерах, и тем самым овладеть личными сведениями, нужно ограничить доступ к компьютерам, на которых выполняется служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Дополнительные сведения см. в разделе [Доступ к службам Integration Services](../access-to-the-integration-services-service.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
 В следующем списке приведены ссылки на разделы, в которых описывается выполнение определенных задач в отношении безопасности.  
  
-   [Создание пользовательской роли](../create-a-user-defined-role.md)  
  
-   [Назначение пакетам роли чтения и модуля записи](../assign-a-reader-and-writer-role-to-a-package.md)  
  
-   [Реализация политики подписывания путем задания параметра реестра](../implement-a-signing-policy-by-setting-a-registry-value.md)  
  
-   [Подписание пакета цифровым сертификатом](../sign-a-package-by-using-a-digital-certificate.md)  
  
-   [Установка и изменение уровня защиты пакетов](../set-or-change-the-protection-level-of-packages.md)  
  
## <a name="see-also"></a>См. также  
 [службы SQL Server Integration Services](../sql-server-integration-services.md)  
  
  
