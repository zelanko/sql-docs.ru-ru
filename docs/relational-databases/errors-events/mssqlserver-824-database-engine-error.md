---
title: MSSQLSERVER_824 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 824 (Database Engine error)
ms.assetid: 2aa22246-2712-4fdb-9744-36e7e6f3175e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e386bad0a14c99b2a1ce82b9db6790534a8473c8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68007015"
---
# <a name="mssqlserver824"></a>MSSQLSERVER_824
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|824|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|B_HARDSSERR|  
|Текст сообщения|SQL Server обнаружил логическую ошибку ввода-вывода, связанную с согласованностью: %ls. Она произошла при %S_MSG страницы %S_PGID в базе данных с идентификатором %d по смещению %#016I64x файла «%ls».  Дополнительные сведения см. в журнале ошибок SQL Server и журнале системных событий.|  
  
## <a name="explanation"></a>Объяснение  
Эта ошибка говорит о следующем: Windows сообщает об успешном считывании страницы с диска, но [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаружил некоторые повреждения страницы. Данная ошибка схожа с ошибкой 823, за исключением того, что в Windows никакие ошибки обнаружены не были. Чаще всего это говорит о проблеме с подсистемой ввода-вывода, например сбое жесткого диска, проблемах с дисковым встроенным ПО, драйверами устройств и т.д. Дополнительные сведения об ошибках ввода-вывода см. в [главе 2 документации Майкрософт об основных операциях ввода-вывода в SQL Server](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)).  
  
## <a name="user-action"></a>Действие пользователя  
  
### <a name="look-for-hardware-failure"></a>Поиск сбоев оборудования  
Выполните диагностику оборудования и исправьте все найденные проблемы. Также просмотрите журнал системы и журналы приложений [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows и журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чтобы определить, была ли ошибка вызвана сбоем оборудования. Исправьте все неполадки оборудования, обнаруженные в журналах.  
  
Если постоянно возникают проблемы с повреждением данных, попробуйте изменить некоторые компоненты оборудования, чтобы локализовать проблему. Убедитесь, что в системе не включено кэширование записи для контроллера дисков. Если есть подозрение, что неполадки вызваны кэшированием записи, обратитесь к поставщику оборудования.  
  
В конце концов можно попробовать сменить оборудование. Это может включать форматирование дисков и переустановку операционной системы.  
  
### <a name="restore-from-backup"></a>Восстановление из резервной копии  
Если проблема не связана с оборудованием и имеется безошибочная резервная копия, восстановите базу данных из этой копии.  
  
Рассмотрите вариант изменения настроек баз данных и включения параметра PAGE_VERIFY CHECKSUM. Дополнительные сведения о PAGE_VERIFY см. в статье [ALTER DATABASE (Transact-SQL)](~/t-sql/statements/alter-database-transact-sql-set-options.md).  
  
## <a name="see-also"></a>См. также:  
[Управление таблицей suspect_pages (SQL Server)](~/relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
