# Advance-programming-assignment-3rd
mockito userservice
import static org.mockito.Mockito.*;
import static org.junit.jupiter.api.Assertions.*;

import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;
import org.mockito.*;

class User {
    private int id;
    private String name;
    private String email;

    public User(int id, String name, String email) {
        this.id = id;
        this.name = name;
        this.email = email;
    }

    public int getId() {
        return id;
    }

    public String getName() {
        return name;
    }

    public String getEmail() {
        return email;
    }
}
interface UserRepository {
    User findById(int id);
}
class UserService {
    private UserRepository userRepository;

    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }

    public User getUserDetails(int userId) {
        return userRepository.findById(userId);
    }
}
public class UserServiceTest {

    @Mock
    private UserRepository userRepository;  
    private UserService userService;  

    @BeforeEach 
    public void setUp() {
        MockitoAnnotations.openMocks(this);  
        userService = new UserService(userRepository);  
    }

    @Test  
    public void testGetUserDetails() {

        User mockUser = new User(1, "ankit", "ankit@aksuniversity.com");
        when(userRepository.findById(1)).thenReturn(mockUser);
                User result = UserService.getUserDetails(1);
             }
    



