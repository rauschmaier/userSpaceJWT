# HTML-Userspace mit JWT absichern
## Prinzip der JWT-basierten Authentifizierung

1. **Benutzeranmeldung:**
   - Der Benutzer meldet sich mit seinen Anmeldeinformationen (z.B. Benutzername und Passwort) bei der Anwendung an.
   - Die Anwendung prüft die Anmeldeinformationen gegen die gespeicherten Daten (z.B. in einer Datenbank).

2. **Token-Generierung:**
   - Bei erfolgreicher Authentifizierung generiert der Server ein JWT.
   - Dieses Token enthält Informationen über den Benutzer (z.B. Benutzer-ID, Rollen) und hat eine begrenzte Gültigkeitsdauer.
   - Das Token wird mit einem geheimen Schlüssel signiert, um seine Integrität und Authentizität zu gewährleisten.

3. **Token-Speicherung:**
   - Das generierte Token wird an den Client (z.B. Browser) gesendet.
   - Der Client speichert das Token, üblicherweise im Local Storage oder in einem Cookie.

4. **Zugriff auf geschützte Ressourcen:**
   - Bei jeder nachfolgenden Anfrage zu geschützten Ressourcen fügt der Client das Token in den Autorisierungs-Header der HTTP-Anfrage ein (z.B. `Authorization: Bearer <token>`).
   - Der Server überprüft das Token auf Gültigkeit und Authentizität.
   - Wenn das Token gültig ist, erhält der Benutzer Zugriff auf die angeforderte Ressource. Andernfalls wird der Zugriff verweigert.

5. **Token-Ablauf und Erneuerung:**
   - JWTs haben eine begrenzte Lebensdauer, nach deren Ablauf der Benutzer sich erneut anmelden muss, um ein neues Token zu erhalten.
   - Es ist auch möglich, ein Refresh-Token zu implementieren, das verwendet werden kann, um ein neues JWT zu erhalten, ohne dass der Benutzer seine Anmeldeinformationen erneut eingeben muss.


### User Registration, User Login and Authorization process.
The diagram shows flow of how we implement User Registration, User Login and Authorization process.

![spring-boot-jwt-authentication-spring-security-flow](spring-boot-jwt-authentication-spring-security-flow.png)
## Aufgabe
im Verzeichnis "frontend" gibt es die index.html, welche nur mittels Authenfizierung zugänglich sein soll.

**Vorbereitung:**
1. Importieren Sie das Maven Projekt lokal
2. Springboor benötigt eine Datenbank. Erstellen Sie eine MySQL Datenbank und passen SIe die application.properties in src/main/resources mit Ihren Daten an.
3. Legen Sie einen Beutzer über den API-Endpoint "localhost:8080/api/auth/signup an (post mit json body: {
    "username": "newUser7",
    "email": "test@mail.de",
    "password": "password123"
}
