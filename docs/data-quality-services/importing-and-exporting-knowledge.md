---
title: Импорт и экспорт знаний | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2012
ms.prod: sql-non-specified
ms.prod_service: data-quality-services
ms.service: ''
ms.component: data-quality-services
ms.reviewer: ''
ms.suite: sql
ms.technology:
- data-quality-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 12537c9d-31e4-40b0-a411-cb343abbe96a
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 121fcc9304e72872f8e06374368bd3637577cb0f
ms.sourcegitcommit: 34766933e3832ca36181641db4493a0d2f4d05c6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="importing-and-exporting-knowledge"></a>Импорт и экспорт набора знаний
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
  
## <a name="related-tasks"></a>Related Tasks  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Построение базы знаний с помощью обнаружения знаний и интерактивного управления знаниями|[Построение базы знаний](../data-quality-services/building-a-knowledge-base.md)|  
|Создание отдельного домена и добавление набора знаний в этот домен.|[Управление доменом](../data-quality-services/managing-a-domain.md)|  
|Создание составного домена и добавление набора знаний в этот домен.|[Управление составным доменом](../data-quality-services/managing-a-composite-domain.md)|  
  
  
