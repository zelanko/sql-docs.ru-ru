---
title: Шаг 3. Изменение значения конфигурации свойства Directory | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ba2a091f-361c-4331-afe2-53b465164c36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 011cd07c0f28f884f460d78d5f2f88631bfe2fd9
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52807506"
---
# <a name="step-3-modifying-the-directory-property-configuration-value"></a>Шаг 3. Изменение значения конфигурации свойства Directory
  В этой задаче предстоит изменить хранимый в файле SSISTutorial.dtsConfig параметр настройки свойства Value переменной уровня пакета `User::varFolderName`. Эта переменная обновляет свойство Directory контейнера "цикл по каждому элементу". Измененное значение будет указывать `New Sample Data` папку, созданную в предыдущей задаче. После изменения параметра настройки конфигурации и выполнения пакета свойство Directory будет обновляться этой переменной с использованием значения из файла конфигурации, а не значения из каталога, первоначально заданного в данном пакете.  
  
### <a name="to-modify-the-configuration-setting-of-the-directory-property"></a>Изменение параметра конфигурации для свойства Directory  
  
1.  В приложении «Блокнот» или другом текстовом редакторе найдите и откройте файл конфигурации SSISTutorial.dtsConfig, созданный в предыдущей задаче с помощью мастера настройки пакета.  
  
2.  Измените значение свойства **ConfiguredValue** элемента в соответствии с путь `New Sample Data` папку, созданную в предыдущей задаче. Не заключайте этот путь в кавычки. Если `New Sample Data` папка находится в корневом каталоге диска (например, C:\\), то обновляемый файл ML должен быть как в следующем примере:  
  
     `<?xml version="1.0"?><DTSConfiguration><DTSConfigurationHeading><DTSConfigurationFileInfo GeneratedBy="DOMAIN\UserName" GeneratedFromPackageName="Lesson 5" GeneratedFromPackageID="{F4475E73-59E3-478F-8EB2-B10AFA61D3FA}" GeneratedDate="6/10/2012 8:16:50 AM"/></DTSConfigurationHeading><Configuration ConfiguredType="Property" Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType="String"><ConfiguredValue></ConfiguredValue></Configuration></DTSConfiguration>`  
  
     Данные заголовка из `GeneratedBy`, `GeneratedFromPackageID`, и **GeneratedDate** будет отличаться в файле, конечно. `Configuration` — элемент, на который необходимо обратить внимание. Свойство `Value` переменной `User::varFolderName` теперь содержит значение «C:\New Sample Data».  
  
3.  Сохраните изменения и закройте текстовый редактор.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Шаг 4. Проверка учебного пакета занятия 5](../integration-services/lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
  
