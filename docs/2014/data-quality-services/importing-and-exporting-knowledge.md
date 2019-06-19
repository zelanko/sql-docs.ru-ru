---
title: Импорт и экспорт знаний | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 12537c9d-31e4-40b0-a411-cb343abbe96a
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 2cc9c9576a6ae2f70f2d54d48471339ec07d0e61
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65480536"
---
# <a name="importing-and-exporting-knowledge"></a>Импорт и экспорт набора знаний
  Создавать базы знаний и домены вы можете непосредственно в приложении [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] либо можно импортировать знания в базу знаний или экспортировать их оттуда. В приложении [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] вы можете использовать файл данных для импорта и экспорта или файл Excel для импорта. Используемый файл данных — это зашифрованный файл с расширением .dqs, созданный службами [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Файлы, созданные Microsoft Excel, могут иметь расширение XLSX, XLS или CSV. Эти операции дают больше гибкости в построении и совместном использовании знаний, которые используются для очистки данных и сопоставления.  
  
> [!IMPORTANT]  
>  Запустив программу DQSInstaller.exe в командной строке, вы можете экспортировать сразу *все* базы знаний на сервере [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] в резервный файл служб DQS (.dqsb). Аналогично, запустив программу DQSInstaller.exe в командной строке, вы можете импортировать сразу *все* базы знаний из резервного файла служб DQS (.dqsb) на сервер [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] . Сведения об этом см. в разделе [Экспорт и импорт баз знаний DQS с помощью DQSInstaller.exe](install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md) в руководстве по установке служб DQS.  
  
## <a name="in-this-section"></a>в этом разделе  
 Вы можете выполнить следующие операции импорта и экспорта.  
  
|||  
|-|-|  
|Экспорт домена из базы знаний в файл данных .dqs.|[Экспорт домена в файл DQS](../../2014/data-quality-services/export-a-domain-to-a-dqs-file.md)|  
|Импорт домена из файла данных .dqs в существующую базу знаний.|[Импорт домена из файла DQS](../../2014/data-quality-services/import-a-domain-from-a-dqs-file.md)|  
|Экспорт всей базы знаний в файл данных .dqs.|[Экспорт базы знаний в файл DQS](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)|  
|Импорт всей базы знаний в файл данных .dqs.|[Импорт базы знаний из файла .dqs](../../2014/data-quality-services/import-a-knowledge-base-from-a-dqs-file.md)|  
|Импорт значений в домен из файла Excel|[Импорт значений в домен из файла Excel](../../2014/data-quality-services/import-values-from-an-excel-file-into-a-domain.md)|  
|Импорт доменов из файла Excel в базу знаний|[Импорт доменов из файла Excel при обнаружении набора знаний](../../2014/data-quality-services/import-domains-from-an-excel-file-in-knowledge-discovery.md)|  
|Импорт знаний, полученных во время очистки, в базу знаний.|[Импорт значений проекта очистки в домен](../../2014/data-quality-services/import-cleansing-project-values-into-a-domain.md)|  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Построение базы знаний с помощью обнаружения знаний и интерактивного управления знаниями|[Построение базы знаний](../../2014/data-quality-services/building-a-knowledge-base.md)|  
|Создание отдельного домена и добавление набора знаний в этот домен.|[Управление доменом](../../2014/data-quality-services/managing-a-domain.md)|  
|Создание составного домена и добавление набора знаний в этот домен.|[Управление составным доменом](../../2014/data-quality-services/managing-a-composite-domain.md)|  
  
  
