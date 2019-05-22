---
title: Заметки о выпуске (Драйвер OLE DB для SQL Server) | Документация Майкрософт
ms.date: 05/13/2019
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: genemi
author: mateusz-kmiecik
ms.author: v-makmie
ms.openlocfilehash: 969caa46506c9fd19410c5ace753076b3ba02fbe
ms.sourcegitcommit: 553ecea0427e4d2118ea1ee810f4a73275b40741
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65619986"
---
# <a name="release-notes-for-the-microsoft-ole-db-driver-for-sql-server"></a>Заметки о выпуске Microsoft OLE DB Driver for SQL Server

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

Эта страница описывает, что было добавлено в каждой версии драйвера Microsoft OLE DB для SQL Server.

<!--
USE THE TABLE FORMAT!
Hello, from now on, please use the table-based format standard for all new Release Notes content.
See section "## 18.2.1" for a live example in this article.
Thank you. For questions, contact GeneMi. (2019/03/16)
-->

## <a name="1822"></a>18.2.2

Май 2019 г.

### <a name="bugs-fixed"></a>Исправлены ошибки

| Исправление ошибки | Сведения |
| :-------- | :------ |
| Исправлена неинтерактивная проверка подлинности Azure Active Directory в многопотоковом подразделении (MTA). | Драйвер OLE DB 18.2.1 некорректно пытается изменить модель параллелизма COM в подразделении, ранее инициализированном как многопотоковое (MTA). В результате, если приложение впоследствии совершает несколько вызовов [CoInitialize](https://go.microsoft.com/fwlink/?linkid=2092520) или [CoInitializeEx](https://go.microsoft.com/fwlink/?linkid=2092521) до вызова интерфейса [IDBInitialize::Initialize](https://go.microsoft.com/fwlink/?linkid=2092522), драйверу не удается подключиться с использованием какой-либо модели проверки подлинности Azure Active Directory. |
| &nbsp; | &nbsp; |

## <a name="1821"></a>18.2.1

Февраль 2019 г.

### <a name="features-added"></a>Добавлены возможности

| Добавленная возможность | Сведения |
| :------------ | :------ |
| Поддержка кодировки UTF-8 на сервере. | &bull; &nbsp; [Поддержка UTF-8 в драйвере OLE DB для SQL Server](features/utf-8-support-in-oledb-driver-for-sql-server.md). |
| Поддержка проверки подлинности Azure Active Directory. | &bull; &nbsp; [Использование Azure Active Directory](features/using-azure-active-directory.md). |
| &nbsp; | &nbsp; |

## <a name="1810"></a>18.1.0

Июль 2018  г.

### <a name="features-added"></a>Добавлены возможности

| Добавленная возможность | Сведения |
| :------------ | :------ |
| Поддержка ключевого слова `UseFMTONLY` для строки подключения, а также свойства инициализации `SSPROP_INIT_USEFMTONLY`. | `UseFMTONLY` определяет способ получения метаданных при подключении к [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более новым версиям.<br/><br/>&bull; &nbsp; [Использование ключевых слов строки подключения с драйвером OLE DB для SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

### <a name="bugs-fixed"></a>Исправлены ошибки

| Исправление ошибки | Сведения |
| :-------- | :------ |
| Исправлена неверная версия файла форматирования BCP. | Драйвер OLE DB 18.0 некорректно задает версию файла форматирования BCP как 18.0 вместо 11.0.<br/><br/>Файлы форматирования, создаваемые драйвером OLE DB 18.0, не могут быть прочитаны драйвером OLE DB 18.1.<br/><br/>Если файлы форматирования, созданные в предыдущей версии драйвера, требуется использовать в новом драйвере, вы можете отредактировать файлы и изменить версию на 11.0 вручную. |
| &nbsp; | &nbsp; |

## <a name="1802"></a>18.0.2

### <a name="features-added"></a>Добавлены возможности

| Добавленная возможность | Сведения |
| :------------ | :------ |
| Поддержка ключевого слова `MultiSubnetFailover` для строки подключения, а также свойства инициализации `SSPROP_INIT_MULTISUBNETFAILOVER`. | &bull; &nbsp; [Поддержка высокого уровня доступности и аварийного восстановления в драйвере OLE DB для SQL Server](features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).<br/><br/>&bull; &nbsp; [Использование ключевых слов строки подключения с драйвером OLE DB для SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

## <a name="see-also"></a>См. также раздел

[Драйвер Microsoft OLE DB для SQL Server](oledb-driver-for-sql-server.md)
