---
title: "Подготовка базы данных Access для миграции (AccessToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-access
ms.custom: 
ms.date: 08/15/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
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
caps.latest.revision: "20"
author: Shamikg
ms.author: Shamikg
manager: murato
ms.workload: On Demand
ms.openlocfilehash: fb7743e870b97882ad2bcec0428b3047f28f538d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="preparing-access-databases-for-migration-accesstosql"></a>Подготовка к миграции (AccessToSQL) базы данных Access
Перед переносом базы данных Access для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], необходимо определить, какие базы данных для миграции и убедитесь, что эти базы данных все готово для миграции.  
  
## <a name="determining-when-to-migrate-to-sql-server"></a>Определение необходимости миграции в SQL Server  
Базы данных Jet, который используется как компонент database engine для доступа, — это гибкий и простой в использовании решение для управления данными. А слишком больших баз данных и дополнительные критически важных, многие пользователи найти что требуют повышения производительности, безопасности и доступности. Для приложений, требующих более надежную платформу данных, рассмотрите перемещение основных баз данных для этих приложений [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Дополнительные сведения о том, когда следует выполнять перенос см. в разделе [страница сведений о миграции](http://go.microsoft.com/fwlink/?LinkId=68571) на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] веб-сайта.  
  
После переноса базы данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], можно продолжать использовать доступ с помощью связанных таблиц, или можно вручную переместить приложения, чтобы [!INCLUDE[msCoName](../../includes/msconame_md.md)] код на основе .NET Framework напрямую взаимодействует с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
## <a name="determining-which-databases-to-migrate"></a>Определить, какие базы данных для миграции  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Для вас Migration Assistant (SSMA) для доступа можно найти базы данных Access. Затем можно экспортировать метаданные об этих базах данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Дополнительные сведения о способах экспорта и запрос метаданных см. в разделе [Экспорт инвентаризацию доступа](http://msdn.microsoft.com/7e1941fb-3d14-4265-aff6-c77a4026d0ed).  

   > [!NOTE]
   > Не все функции доступа и параметры поддерживаются, или можно легко преобразовать, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Перед началом миграции баз данных, в разделе [несовместимые возможности доступа](http://msdn.microsoft.com/99d45b9c-e3b9-4d56-8c25-b594b887ace1).
  
## <a name="preparing-for-migration"></a>Подготовка к миграции  
Следуйте приведенным ниже рекомендациям для подготовки баз данных Access для миграции в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
### <a name="upgrading-older-access-databases"></a>Обновление старых баз данных Access  
SSMA для Access поддерживает Access 97 и более поздних версиях. При наличии баз данных из более ранних версий Access, откройте и сохраните баз данных Microsoft Access 97 или более поздней версии.  
  
### <a name="removing-workgroup-protection"></a>Удаление рабочей группы защиты  
SSMA невозможно выполнить миграцию баз данных, использующих рабочей группы защиты. Чтобы снять защиту рабочей группы в базе данных Access, выполните следующие действия.  
  
1.  Скопируйте файл базы данных Access в другое место.  
  
2.  Откройте скопированной базы данных.  
  
3.  На **средства** последовательно выберите пункты **безопасности**, а затем выберите **разрешения пользователей и групп**.  
  
4.  Выберите **пользователей** выберите **администратора** пользователя и убедитесь, что **Администрирование** задано разрешение.  
  
5.  Выберите **группы** выберите **пользователей** группы, а затем убедитесь, что **Администрирование** задано разрешение.  
  
6.  Нажмите кнопку **ОК**, а затем на **файл** меню, нажмите кнопку **выхода**.  
  
SSMA теперь можно использовать для переноса копии базы данных. После загрузки схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], можно вручную защитить базу данных на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
### <a name="backing-up-databases"></a>Резервное копирование баз данных  
Перед переносом базы данных Access для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], создайте резервную копию обе доступа базы данных, для которого будет миграция а также [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] баз данных, в которых выполняется миграция, доступ к объектам и данным.  
  
Резервное копирование базы данных, на **средства** последовательно выберите пункты **Служебные**, а затем выберите **резервное копирование базы данных**.  
  
Сведения о резервном копировании [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] баз данных, в разделе «Резервное копирование и восстановление баз данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] электронной документации.  
  
### <a name="documenting-databases"></a>Документирование баз данных  
Можно также описываются свойства, такие как списки объектов базы данных, размер файла и разрешений баз данных Access. Для создания этой документации в режиме доступа на **средства** последовательно выберите пункты **анализ**, а затем нажмите кнопку **Documented**.  
  
## <a name="see-also"></a>См. также раздел  
[Миграция баз данных Access в SQL Server](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[Связывание приложения Access в SQL Server](http://msdn.microsoft.com/82374ad2-7737-4164-a489-13261ba393d4)
