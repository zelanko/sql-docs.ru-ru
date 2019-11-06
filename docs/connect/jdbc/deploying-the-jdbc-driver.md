---
title: Развертывание JDBC Driver | Документация Майкрософт
ms.custom: ''
ms.date: 10/28/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3ad3508d-d9b1-47fb-a63b-21cdc3ed44e0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 518f6bd2605d92857520f870b20edcd351771c54
ms.sourcegitcommit: 4fb6bc7c81a692a2df706df063d36afad42816af
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/29/2019
ms.locfileid: "73049838"
---
# <a name="deploying-the-jdbc-driver"></a>Развертывание JDBC Driver
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  При развертывании приложения, зависящего от драйвера [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], необходимо вместе с приложением распространять драйвер JDBC. В отличие от компонентов доступа к данным Windows DAC, которые являются компонентами операционной системы Windows, драйвер JDBC считается компонентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Для развертывания драйвера JDBC в приложении используются два подхода. При использовании одного файлы драйвера JDBC включаются как часть собственного настраиваемого пакета установки. При втором подходе используется предоставляемый Майкрософт пакет установки JDBC, который можно скачать в [Центре разработки драйвера Microsoft JDBC для SQL Server](https://go.microsoft.com/fwlink/?LinkId=70166).  
  
 В следующих разделах описывается использование пакета установки в операционных системах Windows и UNIX.  
  
> [!NOTE]  
>  Дополнительные общие сведения о развертывании приложений Java см. на веб-сайте Java.  
  
## <a name="deploying-the-jdbc-driver-on-windows-systems"></a>Развертывание JDBC Driver в системах Windows  
 При развертывании драйвера JDBC в операционных системах Windows необходимо использовать исполняемый вариант ZIP-файла пакета установки, который обычно называется `sqljdbc_<version>_<language>.exe`.  
  
 Для автоматического запуска исполняемого файла в формате ZIP необходимо использовать параметр командной строки `/auto` в командной строке или пакетном файле, как описано ниже.  
  
 `sqljdbc_<version>_<language>.exe /auto`  
  
> [!NOTE]  
>  При использовании параметра `/auto` установка не будет полностью автоматической, так как на экране пользователя все же будет отображаться диалоговое окно WinZip. Однако оно не требует выполнения каких-либо действий пользователя и закрывается после выполнения операции распаковки.  
  
## <a name="deploying-the-driver-on-unix-systems"></a>Развертывание JDBC Driver в системах UNIX 
 При развертывании драйвера JDBC в операционных системах UNIX необходимо использовать исполняемый файл в формате GZIP пакета установки, который обычно называется `sqljdbc_<version>_<language>.tar.gz`.  
  
 До установки драйвера JDBC необходимо убедиться в том, что в системе пользователя установлены программы gzip и tar, и что папки, содержащие исполняемые файлы обеих программ, добавлены к переменной среды PATH.  
  
 Чтобы распаковать сжатый TAR-файл, перейдите в каталог, в который нужно распаковать драйвер, и введите следующую команду:  
  
 `gzip -d sqljdbc_<version>_<language>.tar.gz`  
  
 Чтобы распаковать TAR-файл, переместите его в каталог, в который нужно установить драйвер, и введите следующую команду:  
  
 `tar -xf sqljdbc_<version>_<language>.tar`  

## <a name="legalities-of-driver-redistribution"></a>Судебное распространение драйверов

Драйверы JDBC версии 6,0, 6,2, 6,4 и 7,0 являются распространяемыми. В лицензионном соглашении ознакомьтесь с разделом _Распространяемый код_.

Драйверы JDBC версии 4. x устарели и являются устаревшими. Срок действия поддержки 4. x истек до 2018.

## <a name="see-also"></a>См. также раздел  
 [Общие сведения о JDBC Driver](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
