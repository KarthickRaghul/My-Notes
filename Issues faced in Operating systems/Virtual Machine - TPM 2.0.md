- **Open Command Prompt**  
    Click the **Back** button to return to the previous setup screen. On your keyboard, press the combination **Shift + F10** to open the Command Prompt.

- **Open Registry Editor**  
    In the Command Prompt window, type `regedit` and press **Enter**.

- **Navigate to the Setup Key**  
    In the Registry Editor, navigate to the following path:  
    `HKEY_LOCAL_MACHINE\SYSTEM\Setup`

- **Create the LabConfig Key**
    
    - Right-click on the **Setup** key.
    
    - Select **New** > **Key**.
    
    - Name the new key `**LabConfig**` (make sure to use a capital 'L' and a capital 'C').
    

- **Create DWORD Values**  
    Go into the newly created `**LabConfig**` key. Inside this key, create two new **DWORD (32-bit) Value** entries:
    
    - **Right-click** in the empty space, select **New** > **DWORD (32-bit) Value**.
        
        - Name the first value: `**BypassTPMCheck**` (Use capital B, T, P, M, and C).
        
        - Double-click `BypassTPMCheck` and set the **Value data** to `**1**`.
        
    
    - **Right-click** again, select **New** > **DWORD (32-bit) Value**.
        
        - Name the second value: `**BypassSecureBootCheck**` (Use capital B, S, B, and C).
        
        - Double-click `BypassSecureBootCheck` and set the **Value data** to `**1**`