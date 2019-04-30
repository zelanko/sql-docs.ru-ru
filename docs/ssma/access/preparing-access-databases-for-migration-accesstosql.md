---
title: Подготовка баз данных Access для миграции (AccessToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 08/15/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Access databases, versions
- Access databases, when to migrate
- Access databases, workgroup security
- backing up databases
- documenting databases
- files, preparing
- migrating databases, versions
- migrating databases, when to migrate
- versions of Access
- workgroup security
ms.assetid: 9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: 9495ff7a58da124255cc6bf5674d92ebeef4c2b0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63299481"
---
# <a name="preparing-access-databases-for-migration-accesstosql"></a>Подготовка баз данных Access для миграции (AccessToSQL)
Прежде чем выполнять миграцию баз данных Access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], необходимо определить, какие базы данных для переноса и убедитесь, что эти базы данных готовы к миграции.  
  
## <a name="determining-when-to-migrate-to-sql-server"></a>Определение условий к переходу на SQL Server  
Базы данных Jet, который используется в качестве ядра базы данных для доступа, — это гибкий и простой в использовании решение для управления данными. Тем не менее слишком больших баз данных и дополнительные критически важна, многие пользователи найти что они требуют повышения производительности, безопасности и доступности. Для приложений, требующих более надежную платформу данных, рассмотрите возможность перехода основных баз данных для этих приложений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения о том, когда следует выполнять перенос см. в разделе [страница сведений о миграции](https://go.microsoft.com/fwlink/?LinkId=68571) на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] веб-сайта.  
  
После переноса базы данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], можно продолжать использовать доступ с помощью связанных таблиц, или можно вручную перенести приложения на [!INCLUDE[msCoName](../../includes/msconame_md.md)] кода на основе .NET Framework, который взаимодействует непосредственно с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="determining-which-databases-to-migrate"></a>Определить, какие базы данных для миграции  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) для доступа можно найти базы данных Access для вас. Затем можно экспортировать метаданные об этих базах данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения о том, как экспортировать и запросить метаданные, см. в разделе [Экспорт инвентаризации Access](exporting-an-access-inventory-accesstosql.md).  

   > [!NOTE]
   > Не все функции доступа и параметры поддерживаются, или может быть просто преобразована, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Перед началом миграции баз данных, см. в разделе [несовместимые возможности доступа](incompatible-access-features-accesstosql.md).
  
## <a name="preparing-for-migration"></a>Подготовка к миграции  
Следуйте приведенным ниже рекомендациям для подготовки базы данных Access к миграции в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="upgrading-older-access-databases"></a>Обновление старых баз данных Access  
SSMA для Access поддерживает Access 97 и более поздних версий. Если у вас есть баз данных из более ранних версиях Access, открывать и сохранять базы данных в Access 97 или более поздней версии.  
  
### <a name="removing-workgroup-protection"></a>Удаление рабочей группы защиты  
SSMA невозможно выполнить миграцию баз данных, использующих рабочей группы защиты. Чтобы снять защиту рабочей базы данных Access, выполните следующие действия.  
  
1.  Скопируйте файл базы данных Access в другое расположение.  
  
2.  Откройте копии базы данных.  
  
3.  На **средства** последовательно выберите пункты **безопасности**, а затем выберите **разрешения пользователей и групп**.  
  
4.  Выберите **пользователей** выберите **администратора** пользователя и убедитесь, что **Администрирование** задано разрешение.  
  
5.  Выберите **группы** выберите **пользователей** группе, а затем убедитесь, что **Администрирование** задано разрешение.  
  
6.  Нажмите кнопку **ОК**, а затем на **файл** меню, щелкните **выхода**.  
  
SSMA теперь можно использовать для переноса копии базы данных. После загрузки схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], вы можете защитить базы данных вручную на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="backing-up-databases"></a>Резервное копирование баз данных  
Перед переносом базы данных Access для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], сделайте резервные копии обе доступа базы данных, которую необходимо перенести, а также [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] баз данных, в которые будут перенесены, доступ к объектам и данным.  
  
Для резервного копирования базы данных, на **средства** последовательно выберите пункты **Служебные**, а затем выберите **резервной копии базы данных**.  
  
Сведения о создании резервной копии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] баз данных, см. в разделе «Резервное копирование и восстановление баз данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]"в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.  
  
### <a name="documenting-databases"></a>Документирование баз данных  
Можно также свойства, такие как списки объектов базы данных, размеров файлов и разрешения, баз данных Access документа. Для создания этой документации в режиме доступа на **средства** последовательно выберите пункты **анализ**, а затем нажмите кнопку **документированное**.  
  
## <a name="see-also"></a>См. также  
[Миграция баз данных Access в SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Связь приложений Access SQL Server](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md)
