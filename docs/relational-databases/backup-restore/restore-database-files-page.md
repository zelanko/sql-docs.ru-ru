---
title: Восстановление базы данных (страница "Файлы") | Документация Майкрософт
description: При восстановлении базы данных в SQL Server используйте страницу "Файлы" диалогового окна "Восстановление базы данных" для выбора конкретных файлов, из которых будет восстановлена база данных.
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql13.swb.restoredb.files.f1
- sql13.swb.restoredb.files.f1 in the code
ms.assetid: 714c36ea-a9f9-43a4-99f9-a6f73d1baf8e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ab1cedc6960052ec8a9007b72d9062b8fc818ab7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85737733"
---
# <a name="restore-database-files-page"></a>Восстановление базы данных (страница «Файлы»)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Используйте страницу **Файлы** диалогового окна **Восстановление базы данных** для выбора конкретных файлов, из которых будет восстановлена база данных.  
  
## <a name="options"></a>Параметры  
  
### <a name="restore-database-files-as"></a>Восстановить файлы базы данных как  
 Используйте, чтобы назначить новый путь к восстановленным файлам и управлять им.  
  
 **Переместить все файлы в папку**  
 Перемещение восстановленных файлов.  
  
|Параметр|Описание|  
|------------|-----------------|  
|**Папка файла данных**|Введите или выполните поиск имени папки файла данных, в которую нужно переместить восстановленный файл или файлы данных.|  
|**Папка файлов журнала**|Введите или выполните поиск файла журнала или папки файлов, в которую нужно переместить восстановленный файл журнала.|  
  
 **Логическое имя файла**  
 Отображает одну строку для каждого восстанавливаемого файла базы данных.  
  
 **Тип файла**  
 Отображает тип файла.  
  
 **Имя исходного файла**  
 Отображает исходный путь к файлу для каждого восстанавливаемого файла базы данных.  
  
 **Восстановить как**  
 Перечисляет имена файлов, в которых будут сохранены восстанавливаемые файлы. Введите или найдите соответствующее имя файла.  
  
## <a name="see-also"></a>См. также:  
 [Восстановление базы данных (страница "Общие")](../../relational-databases/backup-restore/restore-database-general-page.md)   
 [Восстановление базы данных (страница "Параметры")](../../relational-databases/backup-restore/restore-database-options-page.md)   
 [Аргументы инструкции RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-arguments-transact-sql.md)   
 [Определение логического устройства резервного копирования для ленточного накопителя (SQL Server)](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-tape-drive-sql-server.md)   
 [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)  
  
  
