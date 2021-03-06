## ASP.NET Core Sample Application integrated with Sign In Canada

Implements an ASP.NET Core 3.1 Razor Pages application with localization management (it supports English and French). This application is using the OIDC middleware for integration with Sign In Canada.

### Configuration

An OpenID Connect Client needs to be configured with information about the OpenID Connect Provider and client credentials. Sign In Canada team will provide you with the following:

* `authority` - URL of OpenID Connect Provider
* `client_id` and `client_secret` - client credentials registered with OpenID Connect Provider 

You will find the majority of the important code in [Startup.cs] which is where the OpenId Connect Provider is configured.

```csharp
...

    services.AddAuthentication(options => {
        options.DefaultScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = OpenIdConnectDefaults.AuthenticationScheme;
    })
    .AddCookie(options => {
        options.Cookie.Name = "mvccode";
    })
    .AddOpenIdConnect("oidc", options =>
        {
            options.ClientId = "xxx-yyyyy-aaaaaa-bbbbbb";
            options.ClientSecret = "clientsecret";
            options.Authority = "https://xxxxxxxxxx.canada.ca";

            options.ResponseType = "code";
            ...
        }
    );
...
```

Because ClientId and ClientSecret are application secrets, we recommend NOT putting them in files that might accidentally be checked into version control. The [Secret Manager](https://docs.microsoft.com/en-us/aspnet/core/security/app-secrets) is our recommended approach for storing the client secrets.

### How to Contribute

See [CONTRIBUTING.md](CONTRIBUTING.md)

### License

Unless otherwise noted, the source code of this project is covered under Crown Copyright, Government of Canada, and is distributed under the [MIT License](LICENSE).

The Canada wordmark and related graphics associated with this distribution are protected under trademark law and copyright law. No permission is granted to use them outside the parameters of the Government of Canada's corporate identity program. For more information, see [Federal identity requirements](https://www.canada.ca/en/treasury-board-secretariat/topics/government-communications/federal-identity-requirements.html).

______________________

## Exemple d'application ASP.NET Core int??gr??e avec Authenti-Canada

Impl??mente une application ASP.NET Core 3.1 (Razor Pages) avec gestion de localisation (elle prend en charge l'anglais et le fran??ais). Cette application utilise le middleware OIDC pour l'int??gration avec Authenti-Canada.

### Configuration

Un client OpenID Connect doit ??tre configur?? avec des informations sur le fournisseur OpenID Connect et les informations d'identification du client. L'??quipe de Authenti Canada vous fournira les ??l??ments suivants:

* `authority` - URL du fournisseur OpenID Connect
* `client_id` and `client_secret` - informations d'identification du client enregistr??es aupr??s du fournisseur OpenID Connect

Vous trouverez la majorit?? du code important dans [Startup.cs] o?? le fournisseur OpenId Connect est configur??.

```csharp
...

    services.AddAuthentication(options => {
        options.DefaultScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = OpenIdConnectDefaults.AuthenticationScheme;
    })
    .AddCookie(options => {
        options.Cookie.Name = "mvccode";
    })
    .AddOpenIdConnect("oidc", options =>
        {
            options.ClientId = "xxx-yyyyy-aaaaaa-bbbbbb";
            options.ClientSecret = "clientsecret";
            options.Authority = "https://xxxxxxxxxx.canada.ca";

            options.ResponseType = "code";
            ...
        }
    );
...
```

??tant donn?? que ClientId et ClientSecret sont des secrets d???application, nous vous recommandons de NE PAS les placer dans des fichiers qui pourraient ??tre accidentellement archiv??s dans un Syst??me de contr??le de version. Le [Gestionnaire de secrets](https://docs.microsoft.com/fr-ca/aspnet/core/security/app-secrets) est notre approche recommand??e pour stocker les secrets du client.

### Comment contribuer

Voir [CONTRIBUTING.md](CONTRIBUTING.md)

### Licence

Sauf indication contraire, le code source de ce projet est prot??g?? par le droit d'auteur de la Couronne du gouvernement du Canada et distribu?? sous la [licence MIT](LICENSE).

Le mot-symbole ?? Canada ?? et les ??l??ments graphiques connexes li??s ?? cette distribution sont prot??g??s en vertu des lois portant sur les marques de commerce et le droit d'auteur. Aucune autorisation n'est accord??e pour leur utilisation ?? l'ext??rieur des param??tres du programme de coordination de l'image de marque du gouvernement du Canada. Pour obtenir davantage de renseignements ?? ce sujet, veuillez consulter les [Exigences pour l'image de marque](https://www.canada.ca/fr/secretariat-conseil-tresor/sujets/communications-gouvernementales/exigences-image-marque.html).