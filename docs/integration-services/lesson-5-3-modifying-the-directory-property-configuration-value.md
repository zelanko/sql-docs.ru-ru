---
title: Шаг 3. Изменение значения конфигурации свойства "Каталог" | Документация Майкрософт
ms.custom: ''
ms.date: 01/08/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: ba2a091f-361c-4331-afe2-53b465164c36
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0f83ecbec76bfb142da55aa659ce3ef1cc95dad1
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71295900"
---
# <a name="lesson-5-3-modify-the-directory-property-configuration-value"></a>Занятие 5-3. Изменение значения конфигурации свойства "Каталог"

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



В этой задаче предстоит изменить хранимый в файле **SSISTutorial.dtsConfig** параметр конфигурации для задания свойства **Значение** переменной уровня пакета `User::varFolderName`. Эта переменная обновляет свойство **Каталог** контейнера "Цикл ForEach". Измененное значение будет указывать на папку **Новый образец данных**, созданную в предыдущей задаче. После изменения параметра конфигурации и выполнения пакета свойство **Каталог** будет обновляться из переменной файла конфигурации. До этого значение свойства **Каталог** определялось в пакете.  
  
## <a name="modify-the-configuration-setting-of-the-directory-property"></a>Изменение параметра конфигурации для свойства "Каталог"  
  
1.  В Блокноте или другом текстовом редакторе найдите и откройте файл конфигурации **SSISTutorial.dtsConfig**, созданный в предыдущей задаче с помощью мастера настройки пакета.  
  
2.  Измените значение элемента **ConfiguredValue** таким образом, чтобы он соответствовал пути к папке **Новый образец данных** , созданной в предыдущей задаче. Не заключайте этот путь в кавычки. Если папка **Новый образец данных** находится на корневом уровне диска (например, **C:\\** ), то обновляемый файл XML должен выглядеть следующим образом:  
  
    ```
    <?xml version="1.0"?>
    <DTSConfiguration>
      <DTSConfigurationHeading>
        <DTSConfigurationFileInfo GeneratedBy="DOMAIN\UserName" GeneratedFromPackageName="Lesson 5" GeneratedFromPackageID="{F4475E73-59E3-478F-8EB2-B10AFEE1D3FA}" GeneratedDate="6/10/2018 8:16:50 AM"/>
      </DTSConfigurationHeading>
      <Configuration ConfiguredType="Property" 
          Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType="String">
        <ConfiguredValue>C:\New Sample Data</ConfiguredValue>
      </Configuration>
    </DTSConfiguration>  
    ```

    Данные заголовка — **GeneratedBy**, **GeneratedFromPackageID** и **GeneratedDate** — в вашем файле будут иными. **Configuration** — элемент, на который необходимо обратить внимание. Свойство **Значение** переменной (`User::varFolderName`) теперь содержит значение **C:\Новый образец данных**.  
  
3.  Сохраните изменения и закройте текстовый редактор.  
  
## <a name="go-to-next-task"></a>Переход к следующей задаче  
[Шаг 4. Тестирование пакета занятия 5](../integration-services/lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
  
  
