---
title: Установка Microsoft ODBC Driver for SQL Server (macOS)
ms.date: 03/05/2020
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver, installing
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 61bbc198c695ba6e1a0b6a339bfb110108435de8
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921920"
---
# <a name="install-the-microsoft-odbc-driver-for-sql-server-macos"></a>Установка Microsoft ODBC Driver for SQL Server (macOS)

В этой статье объясняется, как установить Microsoft ODBC Driver for SQL Server в macOS. В ней также содержатся инструкции для необязательных средств командной строки для SQL Server (`bcp` и `sqlcmd`) и заголовков разработки unixODBC.

В этой статье приведены команды для установки драйвера ODBC из оболочки bash. Сведения о том, как загрузить пакеты напрямую, см. в разделе [Скачивание драйвера ODBC Driver for SQL Server](../download-odbc-driver-for-sql-server.md).

## <a name="microsoft-odbc-17"></a>Microsoft ODBC 17

Чтобы установить Microsoft ODBC Driver 17 для SQL Server в macOS, выполните следующие команды:

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
HOMEBREW_NO_ENV_FILTERING=1 ACCEPT_EULA=Y brew install msodbcsql17 mssql-tools
```

> [!IMPORTANT]
> Если вы установили пакет `msodbcsql` версии 17, который был доступен непродолжительное время, его следует удалить перед установкой пакета `msodbcsql17`. Это позволит избежать конфликтов. Пакет `msodbcsql17` можно установить параллельно с пакетом `msodbcsql` версии 13.

## <a name="previous-versions"></a>Предыдущие версии

В следующих разделах приведены инструкции по установке предыдущих версий драйвера Microsoft ODBC в macOS.

## <a name="odbc-131"></a><a id="13.1"></a> ODBC 13.1

Используйте следующие команды для установки драйвера Microsoft ODBC Driver 13.1 for SQL Server в OS X 10.11 (El Capitan) и macOS 10.12 (Sierra):

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install msodbcsql@13.1.9.2 mssql-tools@14.0.6.0
```

## <a name="driver-files"></a>Файлы драйвера

Драйвер ODBC в macOS состоит из следующих компонентов.

|Компонент|Description|  
|---------------|-----------------|  
|libmsodbcsql.17.dylib или libmsodbcsql.13.dylib|Файл динамической библиотеки (`dylib`), содержащий все функциональные возможности драйвера. Этот файл устанавливается в папке `/usr/local/lib/`.|  
|`msodbcsqlr17.rll` либо `msodbcsqlr13.rll`|Сопутствующий файл ресурса для библиотеки драйвера. Этот файл устанавливается в папке `[driver .dylib directory]../share/msodbcsql17/resources/en_US/` для версии 17 драйвера и в папке `[driver .dylib directory]../share/msodbcsql/resources/en_US/` для версии 13. | 
|msodbcsql.h|Файл заголовка, содержащий все новые определения, необходимые для использования драйвера.<br /><br /> **Примечание**  . Нельзя сослаться на msodbcsql.h и odbcss.h в одной программе.<br /><br /> Файл msodbcsql.h устанавливается в папке `/usr/local/include/msodbcsql17/` для версии 17 драйвера и в папке `/usr/local/include/msodbcsql/` для версии 13. |
|LICENSE.txt|Текстовый файл с условиями лицензионного соглашения. Этот файл помещается в папку `/usr/local/share/doc/msodbcsql17/` для версии 17 драйвера и в папку `/usr/local/share/doc/msodbcsql/` для версии 13. |
|RELEASE_NOTES|Текстовый файл с заметками о выпуске. Этот файл помещается в папку `/usr/local/share/doc/msodbcsql17/` для версии 17 драйвера и в папку `/usr/local/share/doc/msodbcsql/` для версии 13. |

## <a name="resource-file-loading"></a>Загрузка файла ресурсов

Чтобы драйвер работал, он должен загрузить файл ресурсов. Этот файл имеет имя `msodbcsqlr17.rll` или `msodbcsqlr13.rll` в зависимости от версии драйвера. Файл `.rll` располагается по пути относительно расположения самого драйвера (`so` или `dylib`), указанного в таблице выше. Кроме того, начиная с версии 17.1 драйвер пытается загрузить файл `.rll` из каталога по умолчанию, если его не удалось загрузить по относительному пути. Путь к файлу ресурсов по умолчанию в macOS: `/usr/local/share/msodbcsql17/resources/en_US/`

## <a name="troubleshooting"></a>Устранение неполадок

Если не удается установить подключение к SQL Server с помощью драйвера ODBC, см. статью, посвященную известным проблемам при [устранении неполадок подключения](known-issues-in-this-version-of-the-driver.md#connectivity).

## <a name="next-steps"></a>Дальнейшие действия

После установки драйвера можно попробовать [пример приложения C++ ODBC](../../odbc/cpp-code-example-app-connect-access-sql-db.md). Подробнее о разработке приложений ODBC см. в разделе [Разработка приложений](../../../odbc/reference/develop-app/developing-applications.md).

Дополнительные сведения см. в статьях с [заметками о выпуске](release-notes-odbc-sql-server-linux-mac.md) и [требованиями к системе](system-requirements.md) для драйвера ODBC.
