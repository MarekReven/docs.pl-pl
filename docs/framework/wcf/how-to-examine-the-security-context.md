---
title: "Instrukcje: Badanie kontekstu zabezpieczeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceSecurityContext class
- WCF, security
- Claimset class
ms.assetid: 389b5a57-4175-4bc0-ada0-fc750d51149f
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 72bc3dfcc91cb0fe5b393c9735c83b6331d5e0dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-examine-the-security-context"></a><span data-ttu-id="d2367-102">Instrukcje: Badanie kontekstu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d2367-102">How to: Examine the Security Context</span></span>
<span data-ttu-id="d2367-103">Programowania [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usług, kontekst zabezpieczeń usługi umożliwia określenie szczegółów dotyczących poświadczeń klienta i oświadczeń używany do uwierzytelniania w usłudze.</span><span class="sxs-lookup"><span data-stu-id="d2367-103">When programming [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] services, the service security context enables you to determine details about the client credentials and claims used to authenticate with the service.</span></span> <span data-ttu-id="d2367-104">Jest to zrobić za pomocą właściwości <xref:System.ServiceModel.ServiceSecurityContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="d2367-104">This is done by using the properties of the <xref:System.ServiceModel.ServiceSecurityContext> class.</span></span>  
  
 <span data-ttu-id="d2367-105">Na przykład można pobrać tożsamości bieżącego klienta za pomocą <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> lub <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d2367-105">For example, you can retrieve the identity of the current client by using the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> or the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property.</span></span> <span data-ttu-id="d2367-106">Aby określić, czy klient jest anonimowe, użyj <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d2367-106">To determine whether the client is anonymous, use the <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> property.</span></span>  
  
 <span data-ttu-id="d2367-107">Można również określić, jakie oświadczenia są wykonywane w imieniu klienta przez iteracji w kolekcji oświadczeń w <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d2367-107">You can also determine what claims are being made on behalf of the client by iterating through the collection of claims in the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
### <a name="to-get-the-current-security-context"></a><span data-ttu-id="d2367-108">Aby uzyskać bieżący kontekst zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d2367-108">To get the current security context</span></span>  
  
-   <span data-ttu-id="d2367-109">Dostęp do właściwości statycznej <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> można pobrać bieżącego kontekstu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d2367-109">Access the static property <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> to get the current security context.</span></span> <span data-ttu-id="d2367-110">Sprawdź właściwości bieżącego kontekstu z odwołania.</span><span class="sxs-lookup"><span data-stu-id="d2367-110">Examine any of the properties of the current context from the reference.</span></span>  
  
### <a name="to-determine-the-identity-of-the-caller"></a><span data-ttu-id="d2367-111">Można określić tożsamości wywołującego</span><span class="sxs-lookup"><span data-stu-id="d2367-111">To determine the identity of the caller</span></span>  
  
1.  <span data-ttu-id="d2367-112">Drukowanie wartość <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> i <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d2367-112">Print the value of the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> properties.</span></span>  
  
### <a name="to-parse-the-claims-of-a-caller"></a><span data-ttu-id="d2367-113">Aby przeanalizować oświadczenia obiekt wywołujący</span><span class="sxs-lookup"><span data-stu-id="d2367-113">To parse the claims of a caller</span></span>  
  
1.  <span data-ttu-id="d2367-114">Zwraca bieżącą <xref:System.IdentityModel.Policy.AuthorizationContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="d2367-114">Return the current <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span> <span data-ttu-id="d2367-115">Użyj <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> właściwość, aby powrócić do bieżącego kontekstu zabezpieczeń usługi, a następnie zwraca `AuthorizationContext` przy użyciu <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d2367-115">Use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to return the current service security context, then return the `AuthorizationContext` using the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
2.  <span data-ttu-id="d2367-116">Kolekcja przeanalizować <xref:System.IdentityModel.Claims.ClaimSet> obiekty zwrócone przez <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> właściwość <xref:System.IdentityModel.Policy.AuthorizationContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="d2367-116">Parse the collection of <xref:System.IdentityModel.Claims.ClaimSet> objects returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2367-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2367-117">Example</span></span>  
 <span data-ttu-id="d2367-118">Poniższy przykład służy do drukowania wartości <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> i <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> właściwości bieżącego kontekstu zabezpieczeń i <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> właściwości, wartości zasobów oświadczenia i <xref:System.IdentityModel.Claims.Claim.Right%2A> właściwości każdego oświadczenia w bieżącym zabezpieczeń kontekst.</span><span class="sxs-lookup"><span data-stu-id="d2367-118">The following example prints the values of the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> properties of the current security context and the <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> property, the resource value of the claim, and the <xref:System.IdentityModel.Claims.Claim.Right%2A> property of every claim in the current security context.</span></span>  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d2367-119">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d2367-119">Compiling the Code</span></span>  
 <span data-ttu-id="d2367-120">W kodzie użyto następujących przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="d2367-120">The code uses the following namespaces:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.IdentityModel.Policy>  
  
-   <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a><span data-ttu-id="d2367-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2367-121">See Also</span></span>  
 [<span data-ttu-id="d2367-122">Zabezpieczanie usług</span><span class="sxs-lookup"><span data-stu-id="d2367-122">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="d2367-123">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="d2367-123">Service Identity and Authentication</span></span>](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)