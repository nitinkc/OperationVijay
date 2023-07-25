Certainly! Let's add more protected resources to the Postman collection. For this example, we'll add two additional secure endpoints that require specific roles for authorization.

**Postman Collection for Security API with Keycloak Integration**

1. **Environment Variable:**
   - Create an environment variable for the `base_url`, representing the base URL of your API.

2. **Authentication Request (POST):**
   - Endpoint: `/login`
   - Request Body:
     ```json
     {
       "username": "your_username",
       "password": "your_password"
     }
     ```
   - Save the response token as an environment variable (e.g., `access_token`) for subsequent requests.

3. **Secure Endpoint - Requires Authentication (GET):**
   - Endpoint: `/api/secure-data`
   - Request Header:
     ```json
     {
       "Authorization": "Bearer {{access_token}}"
     }
     ```
   - This endpoint requires the `access_token` obtained from the authentication request.

4. **Secure Endpoint - Requires Role Authorization (GET):**
   - Endpoint: `/api/admin-data`
   - Request Header:
     ```json
     {
       "Authorization": "Bearer {{access_token}}"
     }
     ```
   - This endpoint requires the `access_token`.
   - Implement role-based authorization in your API code to ensure that only users with the "admin" role can access this endpoint.

5. **Secure Endpoint - Requires Role Authorization (GET):**
   - Endpoint: `/api/manager-data`
   - Request Header:
     ```json
     {
       "Authorization": "Bearer {{access_token}}"
     }
     ```
   - This endpoint requires the `access_token`.
   - Implement role-based authorization in your API code to ensure that only users with the "manager" role can access this endpoint.

6. **Secure Endpoint - Requires Role Authorization (GET):**
   - Endpoint: `/api/user-data`
   - Request Header:
     ```json
     {
       "Authorization": "Bearer {{access_token}}"
     }
     ```
   - This endpoint requires the `access_token`.
   - Implement role-based authorization in your API code to ensure that only users with the "user" role can access this endpoint.

7. **Logout Request (POST):**
   - Endpoint: `/logout`
   - Request Body: (Optional, depending on your API's logout implementation)

**Note**: As mentioned earlier, this collection is a basic outline. You will need to replace `your_username` and `your_password` with valid Keycloak user credentials in the authentication request. Additionally, ensure that you replace `"http://your-api-base-url"` with the actual base URL of your API in the `base_url` environment variable.

If you have more protected resources or different role-based authorization requirements, you can add additional secure endpoints to the collection following the same pattern as shown above.

After customizing the collection with your API endpoints and Keycloak configurations, save it in a JSON file and import it into Postman to start testing and accessing your protected resources with Keycloak authentication and role-based authorization.






Assuming you have already set up Spring Security and integrated it with Keycloak for authentication, here's how you can implement the authorization logic:

1. **Define a Custom Authorization Service:**

Create a custom service that checks whether the authenticated user has the required role(s) to access a particular resource ID.

```java
@Service
public class AuthorizationService {

    // Define the required roles for accessing the resource ID.
    private static final List<String> REQUIRED_ROLES = Arrays.asList("admin", "manager");

    public boolean hasAuthorization(Collection<? extends GrantedAuthority> authorities) {
        // Check if any of the user's roles match the required roles.
        for (GrantedAuthority authority : authorities) {
            if (REQUIRED_ROLES.contains(authority.getAuthority())) {
                return true;
            }
        }
        // If no matching role is found, return false indicating unauthorized access.
        return false;
    }
}
```

2. **Create a Custom Authorization Endpoint:**

Create an endpoint in your API where you want to check the authorization for a specific resource ID.

```java
@RestController
public class ResourceController {

    @Autowired
    private AuthorizationService authorizationService;

    @GetMapping("/resources/{resourceId}")
    public ResponseEntity<String> getResource(@PathVariable String resourceId, Authentication authentication) {
        // Get the authenticated user's authorities (roles) from the Authentication object.
        Collection<? extends GrantedAuthority> authorities = authentication.getAuthorities();

        // Check if the user has authorization to access the specified resource ID.
        if (authorizationService.hasAuthorization(authorities)) {
            // If authorized, return the resource data (replace this with your actual implementation).
            String resourceData = "Resource data for resource ID: " + resourceId;
            return ResponseEntity.ok(resourceData);
        } else {
            // If unauthorized, return a 403 Forbidden status.
            return ResponseEntity.status(HttpStatus.FORBIDDEN).body("Unauthorized access");
        }
    }
}
```

3. **Secure the Endpoints with Spring Security:**

In your Spring Security configuration, secure the endpoints that require role-based authorization.

```java
@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .authorizeRequests()
                .antMatchers("/resources/{resourceId}").authenticated()
                .and()
            .oauth2ResourceServer()
                .jwt();
    }
}
```

In this configuration, the endpoint `/resources/{resourceId}` is secured and requires authentication. Spring Security will automatically handle the authorization based on the roles obtained from the JWT token issued by Keycloak during authentication.

Please note that this is a basic example of how to implement role-based authorization in a Spring application. In a real-world scenario, you might have a more sophisticated authorization system and handle resource access control differently.

Ensure that you have properly set up Spring Security with Keycloak and that the roles are correctly mapped in the JWT token. Adjust the code according to your specific application requirements and your Keycloak setup.