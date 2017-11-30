---
title: "Передача файла или отчета (диспетчер отчетов) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
ms.assetid: 79027e11-f4ba-4bfd-bd8c-d334e3da02a1
caps.latest.revision: "42"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 4c41372d28a94a2e8bf0ea86a750c15ea29b2abd
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="upload-a-file-or-report-report-manager"></a>Передача файла или отчета (диспетчер отчетов)
  В диспетчере отчетов предусмотрена функция передачи, позволяющая добавлять отчеты, модели и другие файлы к серверу отчетов без публикации этих элементов из клиентского приложения. Файлы, переданные из файловой системы, сохраняются на сервере отчетов как элементы. Способ сохранения зависит от типа передаваемого файла.  
  
-   RDL-файлы сохраняются как отчеты.  
  
-   SMDL-файлы сохраняются как модели отчетов.  
  
-   Все другие файлы, включая файлы общих источников данных (RDS), передаются как ресурсы. Ресурсы не обрабатываются сервером отчетов, но могут быть просмотрены в диспетчере отчетов, если сервер отчетов поддерживает тип MIME файла.  
  
### <a name="to-upload-a-file-or-report"></a>Передача файла или отчета  
  
1.  Запустите [Диспетчер отчетов (службы Reporting Services в основном режиме)](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896).  
  
2.  В диспетчере отчетов перейдите на страницу **Содержимое** . Перейдите к папке, в которую нужно добавить элемент.  
  
3.  Щелкните **Передать файл**.  
  
4.  Нажмите кнопку **Обзор** для выбора передаваемого файла. Можно выгружать файл определения отчета, изображение, документ и любой другой файл, который нужно сделать доступным на сервере отчетов.  
  
5.  Введите имя нового элемента. Имя элемента может включать пробелы, но не может включать зарезервированные символы: ; ? : @ & = + , $ / * < > |.  
  
6.  Если нужно заменить существующий элемент новым, установите флажок **Перезаписывать существующие элементы**.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Создание, удаление или изменение общего источника данных (диспетчер отчетов)](http://msdn.microsoft.com/library/cd7bace3-f8ec-4ee3-8a9f-2f217cdca9f2)   
 [Страница "Содержимое" (диспетчер отчетов)](http://msdn.microsoft.com/library/6b16869b-158a-4934-9c85-bee934b35378)   
 [Страница "Передача файла" (диспетчер отчетов)](http://msdn.microsoft.com/library/7bb3166f-9374-4449-b66a-ffb77298507d)   
 [Передача файлов в папку](../../reporting-services/report-server/upload-files-to-a-folder.md)  
  
  
