---
title: Заметки о выпуске (драйвер OLE DB Driver for SQL Server)
ms.date: 02/27/2020
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: genemi
author: mateusz-kmiecik
ms.author: v-makmie
ms.openlocfilehash: 2c50ae262516fab757d4de7c254af79f0184ea84
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "80345437"
---
# <a name="release-notes-for-the-microsoft-ole-db-driver-for-sql-server"></a>Заметки о выпуске Microsoft OLE DB Driver for SQL Server

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Эта страница описывает, что было добавлено в каждой версии драйвера Microsoft OLE DB для SQL Server.

<!--
USE THE TABLE FORMAT!
Hello, from now on, please use the table-based format standard for all new Release Notes content.
See section "## 18.2.1" for a live example in this article.
Thank you. For questions, contact GeneMi. (2019/03/16)
-->

## <a name="1830"></a>18.3.0

![скачать](../../ssms/media/download-icon.png) [Скачать установщик x64](https://go.microsoft.com/fwlink/?linkid=2117515)  
![скачать](../../ssms/media/download-icon.png) [Скачать установщик x86](https://go.microsoft.com/fwlink/?linkid=2117517)  

Выпущено: Октябрь 2019 г.

Если необходимо загрузить установщик на языке, отличном от обнаруженного, можно использовать эти прямые ссылки.  
Для драйвера x64: [Китайский (упрощенное письмо)](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x804) | [Китайский (традиционное письмо)](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x40a)  
Для драйвера x86: [Китайский (упрощенное письмо)](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x804) | [Китайский (традиционное письмо)](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x40a)  

### <a name="features-added"></a>Добавлены возможности

| Добавленная возможность | Сведения |
| :------------ | :------ |
| Поддержка проверки подлинности Azure Active Directory (`ActiveDirectoryInteractive`, `ActiveDirectoryMSI`). | [Использование Azure Active Directory](features/using-azure-active-directory.md) |
| Включение библиотеки проверки подлинности Azure Active Directory (adal.dll) в установщик | Теперь Библиотека проверки подлинности Active Directory корпорации Майкрософт для SQL Server включена в базовую установку драйвера, а значит, существующие установки библиотеки будут автоматически обновлены и удалены установщиком OLE DB из списка установленных приложений в Windows. |
| &nbsp; | &nbsp; |

### <a name="bugs-fixed"></a>Исправлены ошибки

| Исправление ошибки | Сведения |
| :-------- | :------ |
| Исправлена логика удаления индекса в [IIndexDefinition::DropIndex](https://go.microsoft.com/fwlink/?linkid=2106448). | Предыдущие версии драйвера OLE DB не умеют удалять индекс первичного ключа, если идентификатор схемы не совпадает с идентификатором владельца этого индекса. |
| &nbsp; | &nbsp; |

## <a name="previous-releases"></a>Предыдущие выпуски

Чтобы скачать предыдущие версии драйвера OLE DB, щелкните заголовки со ссылками в приведенных ниже разделах.

## <a name="1823"></a>18.2.3

![скачать](../../ssms/media/download-icon.png) [Скачать установщик x64](https://go.microsoft.com/fwlink/?linkid=2119554)  
![скачать](../../ssms/media/download-icon.png) [Скачать установщик x86](https://go.microsoft.com/fwlink/?linkid=2119738)  

Выпущено: Июнь 2019 г.

Если необходимо загрузить установщик на языке, отличном от обнаруженного, можно использовать эти прямые ссылки.  
Для драйвера x64: [Китайский (упрощенное письмо)](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x804) | [Китайский (традиционное письмо)](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x40a)  
Для драйвера x86: [Китайский (упрощенное письмо)](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x804) | [Китайский (традиционное письмо)](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x40a)  

### <a name="features-added-in-1823"></a>Возможности, добавленные в 18.2.3

| Добавленная возможность | Сведения |
| :------------ | :------ |
| Поддержка обновления драйверов со съемного носителя SQL Server. | Это обновление включает поддержку обновления драйверов непосредственно со съемного носителя SQL Server. |
| &nbsp; | &nbsp; |

## <a name="1822"></a>18.2.2

![скачать](../../ssms/media/download-icon.png) [Скачать установщик x64](https://go.microsoft.com/fwlink/?linkid=2118512)  
![скачать](../../ssms/media/download-icon.png) [Скачать установщик x86](https://go.microsoft.com/fwlink/?linkid=2118415)  

Выпущено: Май 2019 г.

Если необходимо загрузить установщик на языке, отличном от обнаруженного, можно использовать эти прямые ссылки.  
Для драйвера x64: [Китайский (упрощенное письмо)](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x804) | [Китайский (традиционное письмо)](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x40a)  
Для драйвера x86: [Китайский (упрощенное письмо)](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x804) | [Китайский (традиционное письмо)](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x40a)  

### <a name="bugs-fixed-in-1822"></a>Ошибки, исправленные в 18.2.2

| Исправление ошибки | Сведения |
| :-------- | :------ |
| Исправлена неинтерактивная проверка подлинности Azure Active Directory в многопотоковом подразделении (MTA). | Драйвер OLE DB 18.2.1 некорректно пытается изменить модель параллелизма COM в подразделении, ранее инициализированном как многопотоковое (MTA). В результате, если приложение впоследствии совершает несколько вызовов [CoInitialize](https://go.microsoft.com/fwlink/?linkid=2092520) или [CoInitializeEx](https://go.microsoft.com/fwlink/?linkid=2092521) до вызова интерфейса [IDBInitialize::Initialize](https://go.microsoft.com/fwlink/?linkid=2092522), драйверу не удается подключиться с использованием какой-либо модели проверки подлинности Azure Active Directory. |
| &nbsp; | &nbsp; |

## <a name="1821"></a>18.2.1

![скачать](../../ssms/media/download-icon.png) [Скачать установщик x64](https://go.microsoft.com/fwlink/?linkid=2118511)  
![скачать](../../ssms/media/download-icon.png) [Скачать установщик x86](https://go.microsoft.com/fwlink/?linkid=2118278)  

Выпущено: Февраль 2019 г.

Если необходимо загрузить установщик на языке, отличном от обнаруженного, можно использовать эти прямые ссылки.  
Для драйвера x64: [Китайский (упрощенное письмо)](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x804) | [Китайский (традиционное письмо)](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x40a)  
Для драйвера x86: [Китайский (упрощенное письмо)](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x804) | [Китайский (традиционное письмо)](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x40a)  

### <a name="features-added-in-1821"></a>Возможности, добавленные в 18.2.1

| Добавленная возможность | Сведения |
| :------------ | :------ |
| Поддержка кодировки UTF-8 на сервере. | [Поддержка UTF-8 в OLE DB Driver for SQL Server](features/utf-8-support-in-oledb-driver-for-sql-server.md). |
| Поддержка проверки подлинности Azure Active Directory. | [Использование Azure Active Directory](features/using-azure-active-directory.md) |
| &nbsp; | &nbsp; |

## <a name="1810"></a>18.1.0

![скачать](../../ssms/media/download-icon.png) [Скачать установщик x64](https://go.microsoft.com/fwlink/?linkid=2118506)  
![скачать](../../ssms/media/download-icon.png) [Скачать установщик x86](https://go.microsoft.com/fwlink/?linkid=2118509)  

Выпущено: Июль 2018 г.

Если необходимо загрузить установщик на языке, отличном от обнаруженного, можно использовать эти прямые ссылки.  
Для драйвера x64: [Китайский (упрощенное письмо)](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x804) | [Китайский (традиционное письмо)](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x40a)  
Для драйвера x86: [Китайский (упрощенное письмо)](https://go.microsoft.com/fwlink/?linkid=2118509&2118509=0x804) | [Китайский (традиционное письмо)](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x40a)  

### <a name="features-added-in-1810"></a>Возможности, добавленные в 18.1.0

| Добавленная возможность | Сведения |
| :------------ | :------ |
| Поддержка ключевого слова `UseFMTONLY` для строки подключения, а также свойства инициализации `SSPROP_INIT_USEFMTONLY`. | `UseFMTONLY` определяет способ получения метаданных при подключении к [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более новым версиям.<br/><br/>Дополнительные сведения см. в разделе: [Использование ключевых слов строки подключения с OLE DB Driver for SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

### <a name="bugs-fixed-in-1810"></a>Ошибки, исправленные в 18.1.0

| Исправление ошибки | Сведения |
| :-------- | :------ |
| Исправлена неверная версия файла форматирования BCP. | Драйвер OLE DB 18.0 некорректно задает версию файла форматирования BCP как 18.0 вместо 11.0.<br/>Файлы форматирования, создаваемые драйвером OLE DB 18.0, не могут быть прочитаны драйвером OLE DB 18.1.<br/>Если файлы форматирования, созданные в предыдущей версии драйвера, требуется использовать в новом драйвере, вы можете отредактировать файлы и изменить версию на 11.0 вручную. |
| &nbsp; | &nbsp; |

## <a name="1802"></a>18.0.2

![скачать](../../ssms/media/download-icon.png) [Скачать установщик x64](https://go.microsoft.com/fwlink/?linkid=2118504)  
![скачать](../../ssms/media/download-icon.png) [Скачать установщик x86](https://go.microsoft.com/fwlink/?linkid=2118277)  

Выпущено: Март 2018 г.

Если необходимо загрузить установщик на языке, отличном от обнаруженного, можно использовать эти прямые ссылки.  
Для драйвера x64: [Китайский (упрощенное письмо)](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x804) | [Китайский (традиционное письмо)](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x40a)  
Для драйвера x86: [Китайский (упрощенное письмо)](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x804) | [Китайский (традиционное письмо)](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x40a)  

### <a name="features-added-in-1802"></a>Возможности, добавленные в 18.0.2

| Добавленная возможность | Сведения |
| :------------ | :------ |
| Поддержка ключевого слова `MultiSubnetFailover` для строки подключения, а также свойства инициализации `SSPROP_INIT_MULTISUBNETFAILOVER`. | Дополнительные сведения см. в разделе:<br/>&bull; &nbsp; [Поддержка высокого уровня доступности и аварийного восстановления в OLE DB Driver for SQL Server](features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).<br/>&bull;&nbsp;[Использование ключевых слов строки подключения с OLE DB Driver for SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

## <a name="see-also"></a>См. также раздел

[Драйвер Microsoft OLE DB для SQL Server](oledb-driver-for-sql-server.md)
