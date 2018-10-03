---
title: Импорт и экспорт знаний | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2012
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology:
- data-quality-services
ms.topic: conceptual
ms.assetid: 12537c9d-31e4-40b0-a411-cb343abbe96a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b526e1437b310499a84625b1460ba18570c8513d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47764132"
---
# <a name="importing-and-exporting-knowledge"></a>Импорт и экспорт набора знаний

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Создавать базы знаний и домены вы можете непосредственно в приложении [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] либо можно импортировать знания в базу знаний или экспортировать их оттуда. В приложении [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] вы можете использовать файл данных для импорта и экспорта или файл Excel для импорта. Используемый файл данных — это зашифрованный файл с расширением .dqs, созданный службами [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Файлы, созданные Microsoft Excel, могут иметь расширение XLSX, XLS или CSV. Эти операции дают больше гибкости в построении и совместном использовании знаний, которые используются для очистки данных и сопоставления.  
  
> [!IMPORTANT]  
>  Запустив программу DQSInstaller.exe в командной строке, вы можете экспортировать сразу *все* базы знаний на сервере [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] в резервный файл служб DQS (.dqsb). Аналогично, запустив программу DQSInstaller.exe в командной строке, вы можете импортировать сразу *все* базы знаний из резервного файла служб DQS (.dqsb) на сервер [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] . Сведения об этом см. в разделе [Export and Import DQS Knowledge Bases Using DQSInstaller.exe](../data-quality-services/install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md) в руководстве по установке служб DQS.  
  
## <a name="in-this-section"></a>в этом разделе  
 Вы можете выполнить следующие операции импорта и экспорта.  
  
|||  
|-|-|  
|Экспорт домена из базы знаний в файл данных .dqs.|[Экспорт домена в файл DQS](../data-quality-services/export-a-domain-to-a-dqs-file.md)|  
|Импорт домена из файла данных .dqs в существующую базу знаний.|[Импорт домена из файла DQS](../data-quality-services/import-a-domain-from-a-dqs-file.md)|  
|Экспорт всей базы знаний в файл данных .dqs.|[Экспорт базы знаний в файл DQS](../data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)|  
|Импорт всей базы знаний в файл данных .dqs.|[Импорт базы знаний из файла DQS](../data-quality-services/import-a-knowledge-base-from-a-dqs-file.md)|  
|Импорт значений в домен из файла Excel|[Import Values from an Excel File into a Domain](../data-quality-services/import-values-from-an-excel-file-into-a-domain.md)|  
|Импорт доменов из файла Excel в базу знаний|[Импорт доменов из файла Excel при обнаружении набора знаний](../data-quality-services/import-domains-from-an-excel-file-in-knowledge-discovery.md)|  
|Импорт знаний, полученных во время очистки, в базу знаний.|[Импорт значений проекта очистки в домен](../data-quality-services/import-cleansing-project-values-into-a-domain.md)|  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Построение базы знаний с помощью обнаружения знаний и интерактивного управления знаниями|[Построение базы знаний](../data-quality-services/building-a-knowledge-base.md)|  
|Создание отдельного домена и добавление набора знаний в этот домен.|[Управление доменом](../data-quality-services/managing-a-domain.md)|  
|Создание составного домена и добавление набора знаний в этот домен.|[Управление составным доменом](../data-quality-services/managing-a-composite-domain.md)|  
  
  
