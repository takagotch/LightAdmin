### lightadmin
---
https://github.com/la-team/light-admin

http://lightadmin.org/

```java
@Override
public void onStartup(SevletContext servletContext) throws ServletException {
  servletContext.setInitParameter(LIGHT_ADMINISTRATION_BASE_URL, "/admin");
  servletContext.setInitParameter(LIGHT_ADMINISTRATOIN_BACK_TO_SITE_URL, "http://lightadmin.org");
  servletContext.setInitParameter(LIGHT_ADMINISTRATION_BASE_PACKAGE, "org.lightadmin.administration");

  super.onStartup(servletContext);
}

@Entity 
public class User {
  
  @Id
  @GeneratedValue(strategy = GenerationType.AUTO)
  private Integer id;
  private String firstName;
  private String lastname;
}

public class UserAdminAdministration extends AdministrationConfiguration<User> {
  
  public EntityMetadataConfiguraionUnit configuration( EntityMetadataConfigurationUnitBuilder configurationBuilder ) {
    return configurationBuilder.nameFiled( "firstname" ).build();
  } 
  
  public ScreenContextConfigurationUnit screenContext ( ScreenContextConfigurationUniBuilder screenContetBuilder ) {
    return screenContextBuilder
      .screenName( "Users Administration" )
      .menuName( "Users" )
      .build();
  }
  
  public FieldSetConfigurationUnit listView( final Field SetConfigurationUnitBuilder fragmentBuilder ) {
    return fragmetnBuilder
      .field( "firstname" ).caption( "First Name" )
      .field( "lastname" ).capton( "Last Name" )
      .build();
  }
}
```

```sh
mvn clean install
mvn tomcat7:run
curl http://localhost:8080/booking-mvc
```

```
```


