---
title: Открытие и сохранение файлов с помощью пакетов SSIS, развернутых в Azure | Документы Майкрософт
description: Узнайте, как открывать и сохранять файлы в локальной среде и в Azure при переносе пакетов SSIS, использующих локальные файловые системы, в службы SSIS в Azure.
ms.date: 06/27/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: integration-services
author: swinarko
ms.author: sawinark
ms.reviewer: douglasl
manager: craigg
ms.openlocfilehash: c77d072067799df660ab1c0989eda410480de816
ms.sourcegitcommit: c582de20c96242f551846fdc5982f41ded8ae9f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37065994"
---
# <a name="open-and-save-files-on-premises-and-in-azure-with-ssis-packages-deployed-in-azure"></a>Открытие и сохранение файлов в локальной среде и в Azure с помощью пакетов SSIS, развернутых в Azure

В этой статье описывается, как открывать и сохранять файлы в локальной среде и в Azure при переносе пакетов SSIS, использующих локальные файловые системы, в службы SSIS в Azure.

## <a name="save-temporary-files"></a>Сохранение временных файлов
Если при выполнении отдельного пакета необходимо хранить и обрабатывать временные файлы, для пакетов можно использовать текущую рабочую папку `.` или временную папку `%TEMP%` на узлах Azure-SSIS Integration Runtime.

## <a name="use-on-premises-file-shares"></a>Использование локальных общих папок
Чтобы и далее применять **локальные общие папки** при переносе пакетов, использующих локальные файловые системы, в службы SSIS в Azure, выполните указанные ниже действия.
1.  Перенесите файлы из локальных файловых систем в локальные общие папки.
2.  Присоедините локальные общие папки к виртуальной сети Azure.
3.  Присоедините среду Azure-SSIS IR к той же виртуальной сети. Дополнительные сведения см. в разделе [Присоединение среды выполнения интеграции Azure SSIS к виртуальной сети](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network).
4.  Подключите среду Azure-SSIS IR к локальным общим папкам в той же виртуальной сети, настроив учетные данные для доступа с проверкой подлинности Windows. Дополнительные сведения см. в статье [Подключение к данным и общим папкам с помощью проверки подлинности Windows](ssis-azure-connect-with-windows-auth.md).
5.  Измените локальные пути к файлам в пакетах на UNC-пути, указывающие на локальные общие папки. Например, измените `C:\abc.txt` на `\\<on-prem-server-name>\<share-name>\abc.txt`.

## <a name="use-azure-file-shares"></a>Использование общих папок Azure
Чтобы применять службу **Файлы Azure** при переносе пакетов, использующих локальные файловые системы, в службы SSIS в Azure, выполните указанные ниже действия.
1.  Перенесите файлы из локальных файловых систем в службы файлов Azure. Дополнительные сведения см. на странице [Файлы Azure](https://azure.microsoft.com/services/storage/files/).
2.  Подключите среду Azure-SSIS IR к службе файлов Azure, настроив учетные данные для доступа с проверкой подлинности Windows. Дополнительные сведения см. в статье [Подключение к данным и общим папкам с помощью проверки подлинности Windows](ssis-azure-connect-with-windows-auth.md).
3.  Измените локальные пути к файлам в пакетах на UNC-пути, указывающие на службу файлов Azure. Например, измените `C:\abc.txt` на `\\<storage-account-name>.file.core.windows.net\<share-name>\abc.txt`.
