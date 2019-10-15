---
title: Заметки о выпуске ODBC для SQL Server в Windows | Документация Майкрософт
ms.custom: ''
ms.date: 02/27/2019
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b8459ed8-625e-4d8b-891c-e7e78c9977cc
ms.reviewer: v-jizho2, v-chojas, genemi
author: v-makouz
ms.author: v-makouz
manager: kenvh
ms.openlocfilehash: 98e7aec7883bc12d04ce24aba7b9a93244f707f6
ms.sourcegitcommit: 512acc178ec33b1f0403b5b3fd90e44dbf234327
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/08/2019
ms.locfileid: "72041161"
---
# <a name="release-notes-for-odbc-to-sql-server-on-windows"></a>Заметки о выпуске ODBC для SQL Server в Windows

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

В этих заметках о выпуске описываются новые возможности Microsoft ODBC Driver for SQL Server в Windows.

<!--
PLEASE USE THE STANDARD 2-COLUMN TABLE FORMAT!

For all our Release Notes articles (What's New too?), we are standardizing on the 2-column format that you see here for version "## 17.3".

Going forward, all new additions to this article must use the 2-column format.

Also, use the shorter ## H2 title format, which eliminates all the redundant constants, and appends the date-added.
One beneift of shortness is the avoidance of the annoying wrapping of unnecessarily long H2 titles in the rightNav.
- OLD H2:  ## What's New in the [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17.3 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on Windows
- NEW H2:  ## 17.3, February 2019

By the way, in GitHub, the file name is changing today 2019/03/30:
- FROM:  docs/connect/odbc/windows/release-notes.md
- TO  :  docs/connect/odbc/windows/release-notes-odbc-sql-server-windows.md

Thank you.
GeneMi (and CraigG).  2019/03/30.
-->

## <a name="1742-october-2019"></a>17.4.2, октябрь 2019 г.

| Добавленная возможность | Сведения |
| :------------ | :------ |
| Поддержка дополнительных конечных точек Azure Key Vault | См. сведения об [использовании функции Always Encrypted с драйвером ODBC](../using-always-encrypted-with-the-odbc-driver.md). |
| Поддержка настройки версии классификации данных | См. статью [Классификация данных](../data-classification.md#bkmk-version). |
| Теперь драйвер будет устанавливать библиотеку проверки подлинности Azure Active Дриректори (ADAL. dll), используемую для проверки подлинности в Azure. | |
| Исправления ошибок. | См. статью [Исправления ошибок](../bug-fixes.md). |
| &nbsp; | &nbsp; |

## <a name="174-july-2019"></a>17.4, июль 2019 г.

| Добавленная возможность | Сведения |
| :------------ | :------ |
| Always Encrypted с безопасными анклавами | См. сведения об [использовании функции Always Encrypted с драйвером ODBC](../using-always-encrypted-with-the-odbc-driver.md). |
| Настраиваемые параметры проверки активности TCP. | См. сведения о [подключении к SQL Server](../linux-mac/connection-string-keywords-and-data-source-names-dsns.md). |
| Исправления ошибок. | См. статью [Исправления ошибок](../bug-fixes.md). |
| &nbsp; | &nbsp; |

## <a name="173-february-2019"></a>Версия 17.3, февраль 2019 г.

| Добавленная возможность | Сведения |
| :------------ | :------ |
| Режим проверки подлинности Управляемого удостоверения службы Azure Active Directory (назначаемого системой и пользователем). | См. статью [Использование Azure Active Directory с драйвером ODBC](../using-azure-active-directory.md). |
| Возможность передавать входные параметры в потоковом режиме для столбцов Always Encrypted. | См. раздел [Ограничения драйвера ODBC при использовании Always Encrypted](../using-always-encrypted-with-the-odbc-driver.md#limitations-of-the-odbc-driver-when-using-always-encrypted). |
| Распределенные транзакции XA. | [Использование транзакций XA](../use-xa-with-dtc.md). |
| Исправления ошибок. | См. статью [Исправления ошибок](../bug-fixes.md). |
| &nbsp; | &nbsp; |

## <a name="172-july-2018"></a>Версия 17.2, июль 2018 г.

| Добавленная возможность | Сведения |
| :------------ | :------ |
| Классификация данных для Базы данных SQL Azure и SQL Server. | См. статью [Классификация данных](../data-classification.md). |
| Поддержка кодировки UTF-8 на сервере. | &nbsp; |
| Исправления ошибок. | См. статью [Исправления ошибок](../bug-fixes.md). |
| &nbsp; | &nbsp; |

## <a name="171-march-2018"></a>Версия 17.1, март 2018 г.

| Добавленная возможность | Сведения |
| :------------ | :------ |
| Поддержка атрибутов подключения `SQL_COPT_SS_CEKCACHETTL` и `SQL_COPT_SS_TRUSTEDCMKPATHS`. | &bull; &nbsp; `SQL_COPT_SS_CEKCACHETTL`<br/>Позволяет управлять временем существования локального кэша для ключей шифрования столбцов, а также освобождать его.<br/><br/>&bull; &nbsp; `SQL_COPT_SS_TRUSTEDCMKPATHS`<br/>Позволяет приложению ограничивать главные ключи столбцов, используемые для операций Always Encrypted, определенным списком.<br/><br/> Дополнительные сведения см. в статье [Использование функции Always Encrypted с драйвером ODBC для SQL Server](../using-always-encrypted-with-the-odbc-driver.md). |
| Поддержка интерактивной проверки подлинности Azure Active Directory | &nbsp; |
| Исправления ошибок. | См. статью [Исправления ошибок](../bug-fixes.md). |
| &nbsp; | &nbsp; |

## <a name="17-february-2018"></a>Версия 17, февраль 2018 г.

| Добавленная возможность | Сведения |
| :------------ | :------ |
| Поддержка Always Encrypted для API BCP. | &nbsp; |
| Новый атрибут строки подключения `UseFMTOnly`. | Предписывает драйверу использовать старые метаданные в особых случаях, в которых требуются временные таблицы. |
| Поддержка Управляемого экземпляра SQL Azure. | Расширенная закрытая предварительная версия.<br/><br/>См. список [отличий при использовании Управляемого экземпляра (ODBC версии 17)](#diffs-managed-instance-17). |
| &nbsp; | &nbsp; |

| Изменение зависимости | Сведения |
| :------------ | :------ |
| Удален помощник по входу в Microsoft Online Services. | Зависимость удалена. |
| &nbsp; | &nbsp; |

### <a name="diffs-managed-instance-17"></a> Отличия при использовании Управляемого экземпляра (ODBC версии 17)

В этой версии ODBC имеется поддержка Управляемого экземпляра SQL Azure (расширенная закрытая предварительная версия). Ниже представлен список отличий при использовании Управляемого экземпляра.

> [!NOTE]
> При использовании Управляемого экземпляра есть ряд особенностей.
>
> - FILESTREAM не поддерживается.
> - Доступ к локальной файловой системе не поддерживается, однако требуется, например, для файлов трассировки.
> - Создание пользовательских типов по локальным путям не поддерживается.
> - Встроенная проверка подлинности Windows не поддерживается.
> - DTC не поддерживается.
> - Учетная запись `sa` отсутствует (учетная запись по умолчанию называется `cloudSA`).
> - В ошибке токена TDS (0xAA) возвращается неправильное имя сервера.
> - Специальные символы в имени базы данных не поддерживаются.
> - Инструкция ALTER DATABASE [имя_БД1] MODIFY NAME = [имя_БД2] не поддерживается.
> - Сообщения об ошибках всегда выводятся на английском языке независимо от выбранного языка (так же как в Azure).

## <a name="131"></a>Версия 13.1

| Добавленная возможность | Сведения |
| :------------ | :------ |
| В драйвере ODBC 13.1 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] добавлена поддержка [Always Encrypted](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md) и [Azure Active Directory](../../../connect/odbc/using-azure-active-directory.md). | Поддержка этих функций доступна при подключении к Microsoft SQL Server 2016 или более поздней версии. |
| Появились ключевые слова и атрибуты для пулов соединений, соответствующие поддержке Always Encrypted и Azure Active Directory. | Эти ключевые слова и атрибуты описываются в статье [Организация пулов соединений с учетом драйвера в ODBC Driver для SQL Server](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

## <a name="13"></a>13

| Добавленная возможность | Сведения |
| :------------ | :------ |
| Добавлена поддержка Microsoft SQL Server 2016. | Сохраняются функциональные возможности драйвера ODBC версии 11. |
| &nbsp; | &nbsp; |

## <a name="11"></a>11

| Добавленная возможность | Сведения |
| :------------ | :------ |
| Появились новые возможности. | См. статью [Функции Microsoft ODBC Driver for SQL Server в Windows](features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md). |
| Включены все возможности, имевшиеся в ODBC для SQL Server 2012 Native Client. | &nbsp; |
| &nbsp; | &nbsp; |
