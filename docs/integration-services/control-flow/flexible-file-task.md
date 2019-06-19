---
title: Задача "Гибкая работа с файлами" | Документация Майкрософт
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPEXTFILETASK.F1
- SQL14.DTS.DESIGNER.AFPEXTFILETASK.F1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2d01304a36f7676f53ffef3f6c6e3c600cb87cb6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66411101"
---
# <a name="flexible-file-task"></a>Задача "Гибкая работа с файлами"

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

Задача "Гибкая работа с файлами" позволяет пользователям выполнять операции с файлами в различных поддерживаемых службах хранилища.
Сейчас поддерживаются службы хранилища

- Локальная файловая система
- [Хранилище BLOB-объектов Azure](https://azure.microsoft.com/services/storage/blobs/)
- [Azure Data Lake Storage 2-го поколения](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction)

Задача "Гибкая работа с файлами" входит в состав [пакета дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Чтобы добавить в пакет задачу "Гибкая работа с файлами", перетащите ее с панели элементов SSIS на панель холста конструктора. Затем дважды щелкните задачу или щелкните ее правой кнопкой мыши и выберите **Изменить**, чтобы открыть диалоговое окно **редактора задачи "Гибкая работа с файлами"** .

Файловая операция, которая будет выполнена, задается свойством **Операция**.
Сейчас поддерживается только **Копирование**.

Для операции **Копирование** доступны следующие свойства.

- **SourceConnectionType**. Определяет тип диспетчера подключений к источникам.
- **SourceConnection**. Определяет диспетчер подключений к источникам.
- **SourceFolderPath**. Указывает путь к папке источника.
- **SourceFileName**. Указывает имя файла источника. Если оставить его пустым, будет скопирована исходная папка.
- **SearchRecursively.** Указывает, следует ли рекурсивно копировать вложенные папки.
- **DestinationConnectionType**. Определяет тип диспетчера подключений к назначениям.
- **DestinationConnection**. Определяет диспетчер подключений к назначениям.
- **DestinationFolderPath**. Указывает путь к папке назначения.
- **DestinationFileName**. Указывает имя файла назначения.
