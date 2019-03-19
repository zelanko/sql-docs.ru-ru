---
title: Заметки о выпуске (Драйвер OLE DB для SQL Server) | Документация Майкрософт
ms.date: 02/13/2019
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: genemi
author: mateusz-kmiecik
ms.author: v-makmie
ms.openlocfilehash: 2a1d6d216f4f7ec7fee0f5f9aa5810c78f1936e6
ms.sourcegitcommit: 03870f0577abde3113e0e9916cd82590f78a377c
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2019
ms.locfileid: "58161771"
---
# <a name="release-notes-for-the-microsoft-ole-db-driver-for-sql-server"></a>Заметки о выпуске Microsoft OLE DB Driver для SQL Server

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

На этой странице описаны, что был добавлен в каждую версию драйвера Microsoft OLE DB для SQL Server.

<!--
USE THE TABLE FORMAT!
Hello, from now on, please use the table-based format standard for all new Release Notes content.
See section "## 18.2.1" for a live example in this article.
Thank you. For questions, contact GeneMi. (2019/03/16)
-->

## <a name="1821"></a>18.2.1

<!--
USE THE TABLE FORMAT!
Hello, from now on, please use the table-based format standard for all new Release Notes content.
See section "## 18.2.1" for a live example in this article.
Thank you. For questions, contact GeneMi. (2019/03/16)
-->

Февраль 2019 г.

### <a name="features-added"></a>Функции, добавленные

| Включена функция | Сведения |
| :------------ | :------ |
| Поддержка кодировки UTF-8 server. | &bull; &nbsp; [Поддержка UTF-8 в драйвере OLE DB для SQL Server](features/utf-8-support-in-oledb-driver-for-sql-server.md). |
| Поддержка проверки подлинности Azure Active Directory. | &bull; &nbsp; [Использование Azure Active Directory](features/using-azure-active-directory.md). |
| &nbsp; | &nbsp; |

## <a name="1810"></a>18.1.0

Июль 2018  г.

### <a name="features-added"></a>Функции, добавленные

| Включена функция | Сведения |
| :------------ | :------ |
| Поддержка `UseFMTONLY` ключевое слово строки подключения, а также для `SSPROP_INIT_USEFMTONLY` свойство инициализации. | `UseFMTONLY` Определяет, как метаданные извлекаются при соединении с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версиях.<br/><br/>&bull; &nbsp; [Использование ключевых слов строки подключения с драйвером OLE DB для SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

### <a name="bugs-fixed"></a>Ошибки, исправленные

| Исправление ошибки | Сведения |
| :-------- | :------ |
| Фиксированный неправильная версия файла формата BCP. | Неправильно 18.0 драйвера OLE DB задает версию файла формата BCP для 18.0, вместо 11.0.<br/><br/>Формат файлов, создаваемых 18.0 драйвера OLE DB не может быть прочитан 18.1 драйвера OLE DB.<br/><br/>Если вам нужно использовать файлы форматирования, созданный в предыдущей версии драйвера с помощью нового драйвера, можно вручную изменить файлы, чтобы изменить версию 11.0. |
| &nbsp; | &nbsp; |

## <a name="1802"></a>18.0.2

### <a name="features-added"></a>Функции, добавленные

| Включена функция | Сведения |
| :------------ | :------ |
| Поддержка `MultiSubnetFailover` ключевое слово строки подключения и `SSPROP_INIT_MULTISUBNETFAILOVER` свойство инициализации. | &bull; &nbsp; [Поддержка высокого уровня доступности и аварийного восстановления в драйвере OLE DB для SQL Server](features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).<br/><br/>&bull; &nbsp; [Использование ключевых слов строки подключения с драйвером OLE DB для SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

## <a name="see-also"></a>См. также раздел

[Драйвер Microsoft OLE DB для SQL Server](oledb-driver-for-sql-server.md)
