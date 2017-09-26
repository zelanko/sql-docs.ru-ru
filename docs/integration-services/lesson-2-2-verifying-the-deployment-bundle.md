---
title: "Шаг 2: Проверка пакета развертывания | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 6c13f5c9-c75e-4e52-94dc-2d2db2c578fe
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 20d8b11e28f7e26e5b61662d8340ab6dbfcc0b95
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="lesson-2-2---verifying-the-deployment-bundle"></a>Занятие 2 2-Проверка пакета развертывания
На занятии 1 был создан проект учебного развертывания и в него добавлены пакеты и вспомогательные файлы; в предыдущей задаче была построена программа развертывания для проекта.  
  
В этой задаче будет проверено содержимое пакета развертывания. Пакет развертывания представляет собой папку, которая будет скопирована на целевой компьютер и использована для установки пакетов. Если было использовано значение по умолчанию — bin\Deployment — в качестве местонахождения для программы развертывания, пакетом развертывания будет папка Bin\Deployment в папке Deployment Tutorial в проекте [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
### <a name="to-verify-the-content-of-deployment-bundle"></a>Проверка содержимого пакета развертывания  
  
1.  Выберите папку bin\Deployment.  
  
2.  Проверьте наличие в папке следующих файлов:  
  
    -   DataTransfer.dtsx  
  
    -   datatransferconfig.dtsconfig  
  
    -   Deployment Tutorial.SSISDeploymentManifest  
  
    -   LoadXMLData.dtsx  
  
    -   loadxmldataconfig.dtsconfig  
  
    -   NewCustomers.txt  
  
    -   orders.xml  
  
    -   orders.xsd  
  
    -   Readme.txt  
  
3.  Щелкните правой кнопкой файл Deployment Tutorial.SSISDeploymentManifest, наведите указатель на пункт **Открыть с помощью**и выберите пункт **Internet Explorer**. Файл также можно открыть в текстовом редакторе, например в приложении «Блокнот». Код XML в файле должен быть таким:  
  
    `<?xml version="1.0"?><DTSDeploymentManifest GeneratedBy="Domain\UserName" GeneratedFromProjectName="Deployment Tutorial" GeneratedDate="2006-02-24T13:29:02.6537669-08:00" AllowConfigurationChanges="true"><Package>DataTransfer.dtsx</Package><Package>LoadXMLData.dtsx</Package><ConfigurationFile>datatransferconfig.dtsconfig</ConfigurationFile><ConfigurationFile>loadxmldataconfig.dtsconfig</ConfigurationFile><MiscellaneousFile>Readme.txt</MiscellaneousFile><MiscellaneousFile>orders.xml</MiscellaneousFile><MiscellaneousFile>NewCustomers.txt</MiscellaneousFile><MiscellaneousFile>orders.xsd</MiscellaneousFile></DTSDeploymentManifest>`  
  
4.  Убедитесь в том, что значение атрибута **AllowConfigurationChanges** равно **true** , а код XML включает элемент **Package** для каждого из двух пакетов, элемент **MiscellaneousFile** для каждого из четырех непакетных файлов и элемент **ConfigurationFile** для каждого из двух XML-файлов конфигурации.  
  
5.  Закройте обозреватель Internet Explorer или текстовый редактор.  
  
## <a name="next-lesson"></a>Следующее занятие  
[Занятие 3. Установка пакетов SSIS](../integration-services/lesson-3-install-ssis-packages.md)  
  
  
  

