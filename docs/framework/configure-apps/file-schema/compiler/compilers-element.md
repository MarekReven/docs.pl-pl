---
title: "&lt;kompilatory&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bea78fe5086a73e4cc588973764ac9bbef2fadc4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltcompilersgt-element"></a><span data-ttu-id="2a34a-102">&lt;kompilatory&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="2a34a-102">&lt;compilers&gt; Element</span></span>
<span data-ttu-id="2a34a-103">Kontener dla elementy kompilatora konfiguracji; zawiera zero lub więcej [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="2a34a-103">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>  
  
 <span data-ttu-id="2a34a-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="2a34a-104">\<configuration></span></span>  
<span data-ttu-id="2a34a-105">\<System.CodeDom — ></span><span class="sxs-lookup"><span data-stu-id="2a34a-105">\<system.codedom></span></span>  
<span data-ttu-id="2a34a-106">\<kompilatory > — Element</span><span class="sxs-lookup"><span data-stu-id="2a34a-106">\<compilers> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a34a-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a34a-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a34a-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2a34a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2a34a-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2a34a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a34a-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2a34a-110">Attributes</span></span>  
 <span data-ttu-id="2a34a-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="2a34a-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2a34a-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2a34a-112">Child Elements</span></span>  
  
|<span data-ttu-id="2a34a-113">Element</span><span class="sxs-lookup"><span data-stu-id="2a34a-113">Element</span></span>|<span data-ttu-id="2a34a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="2a34a-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a34a-115">\<Kompilator > — Element</span><span class="sxs-lookup"><span data-stu-id="2a34a-115">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="2a34a-116">Określa atrybuty kompilatora konfiguracji dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="2a34a-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2a34a-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2a34a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2a34a-118">Element</span><span class="sxs-lookup"><span data-stu-id="2a34a-118">Element</span></span>|<span data-ttu-id="2a34a-119">Opis</span><span class="sxs-lookup"><span data-stu-id="2a34a-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a34a-120">\<Konfiguracja > — Element</span><span class="sxs-lookup"><span data-stu-id="2a34a-120">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="2a34a-121">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2a34a-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="2a34a-122">\<System.CodeDom — > — Element</span><span class="sxs-lookup"><span data-stu-id="2a34a-122">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="2a34a-123">Określa ustawienia kompilatora konfiguracji dla dostawcy dostępnych języków.</span><span class="sxs-lookup"><span data-stu-id="2a34a-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a34a-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2a34a-124">Remarks</span></span>  
 <span data-ttu-id="2a34a-125">[ \<Compilers >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element zawiera ustawienia kompilatora konfiguracji dostawcy języka na komputerze.</span><span class="sxs-lookup"><span data-stu-id="2a34a-125">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="2a34a-126">Każdy [ \<kompilatora >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element określa atrybuty kompilatora konfiguracji dostawcy języka.</span><span class="sxs-lookup"><span data-stu-id="2a34a-126">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="2a34a-127">.NET Framework definiuje ustawienia dostawcy języka i kompilatora początkowej w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="2a34a-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="2a34a-128">Deweloperom i dostawcom kompilatora, można dodać ustawienia konfiguracji nowej <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementacji.</span><span class="sxs-lookup"><span data-stu-id="2a34a-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="2a34a-129">Użyj <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> metody wyliczyć programowo języka ustawienia konfiguracji dostawcy i kompilator na komputerze.</span><span class="sxs-lookup"><span data-stu-id="2a34a-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="2a34a-130">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2a34a-130">Configuration File</span></span>  
 <span data-ttu-id="2a34a-131">Ten element może być użyty w pliku konfiguracji komputera i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2a34a-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a34a-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a34a-132">Example</span></span>  
 <span data-ttu-id="2a34a-133">Poniższy przykład przedstawia element kompilatora typowych konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2a34a-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler   
          language="c#;cs;csharp"   
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""    
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a34a-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a34a-134">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="2a34a-135">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2a34a-135">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="2a34a-136">Schemat ustawień dostawcy języka i kompilatora</span><span class="sxs-lookup"><span data-stu-id="2a34a-136">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [<span data-ttu-id="2a34a-137">\<Kompilator > — Element</span><span class="sxs-lookup"><span data-stu-id="2a34a-137">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)