# Linux_assignment-

#!/bin/bash

# --- Student Details ---
# Name: Advait
# Roll No: 4
# Username: advait

# 1. Initial Setup
mkdir -p ev4
cd ev4
mkdir -p 4
cd 4
echo "Current Path: $(pwd)"

# 2. Navigation Shortcuts
cd - > /dev/null
cd - > /dev/null
cd .
cd ..
cd ~
cd /
ls -l
cd media
cd ~
pwd

# 3. Handling Absolute vs Relative Path (Failure Case)
echo "Attempting relative cd to media from home..."
cd media 2>/dev/null || echo "Inference: cd media failed because it is a relative path."
cd /media
ls -l
ls -al

# 4. File Operations
cd ~/ev4/4
mkdir -p emptydummy
mkdir -p dummy
cd dummy
touch file1
touch file2
ls -l
# Simulating rm -i by skipping the prompt in a script
rm file2 
ls -l
cd ..

# 5. Directory Deletion & Error Handling
rm emptydummy 2>/dev/null || echo "Inference: rm failed on directory without -r."
rmdir emptydummy
rmdir dummy 2>/dev/null || echo "Inference: rmdir failed because dummy contains file1."
rm -r dummy

# 6. Redirection & Content
echo "My first line" > file1.txt
echo "Hello Second line" > file2.txt
echo "Hello line" > file3.txt
cat file1.txt file2.txt > file_combined.txt
# Append
cat file3.txt >> file_combined.txt
# Search
grep -i hello file*
# Copy & Move
cp file1.txt ~/ev4
mv file_combined.txt combined

# 7. Permissions (Logic: 4=Read, 2=Write, 1=Execute)
chmod u+x combined
chmod g-r combined
chmod 777 combined

# 8. User Management (Requires sudo)
echo "The following user commands require sudo privileges:"
# sudo useradd alice
# sudo passwd alice
# sudo userdel alice

# 9. Messaging
echo "Functionality Note:"
echo "'write advait' - Initiates a message to user advait."







# Linux System Administration: Lab Assignment

**Student Details**
* **Name:** Advait
* **Roll No:** 4
* **Username:** advait

---

## Part 1: Directory Navigation and Path Logic

### 1. Initial Setup
**Command: mkdir ev4** **Resultant Directory Path:** `/home/advait`  
> **Inference:** The `mkdir` command creates a new directory. This serves as the root folder for the lab "ev4".

**Command: cd ev4** **Resultant Directory Path:** `/home/advait/ev4`  
> **Inference:** The `cd` command shifts the shell's focus into the specified folder.

**Command: mkdir 4** **Resultant Directory Path:** `/home/advait/ev4`  
> **Inference:** Creates a subdirectory named "4" (the student's roll number) to keep work organized.

**Command: cd 4** **Resultant Directory Path:** `/home/advait/ev4/4`  
> **Inference:** Navigating into the roll number directory, which is now our primary workspace.

---

### 2. Advanced Navigation Techniques
**Command: cd -** **Resultant Directory Path:** `/home/advait/ev4`  
> **Inference:** The `-` argument returns the user to the "Previous Working Directory."

**Command: cd -** **Resultant Directory Path:** `/home/advait/ev4/4`  
> **Inference:** Toggling back again returns us to the roll number directory.

**Command: cd .** **Resultant Directory Path:** `/home/advait/ev4/4`  
> **Inference:** The single dot `.` represents the "current directory." The path remains unchanged.

**Command: cd ..** **Resultant Directory Path:** `/home/advait/ev4`  
> **Inference:** The double dot `..` represents the "parent directory," moving the user one level up.

**Command: cd ~** **Resultant Directory Path:** `/home/advait`  
> **Inference:** The tilde `~` is a shortcut for the user's Home Directory.

**Command: cd /** **Resultant Directory Path:** `/`  
> **Inference:** This moves the user to the Root Directory, the absolute top of the filesystem.

**Command: ls -l** **Resultant Directory Path:** `/`  
> **Inference:** Lists the root contents in "long format," showing system-level folders.

**Command: cd media** **Resultant Directory Path:** `/media`  
> **Inference:** Moves into the `media` directory using a relative path.

**Command: cd** **Resultant Directory Path:** `/home/advait`  
> **Inference:** Typing `cd` with no arguments instantly returns the user to their Home Directory.

**Command: pwd** **Resultant Directory Path:** `/home/advait`  
> **Inference:** Print Working Directory displays the full absolute path.

**Command: cd media** **Resultant Directory Path:** `/home/advait`  
> **Inference:** This fails because there is no folder named `media` inside the home directory. Relative paths depend on current location.

**Command: cd /media** **Resultant Directory Path:** `/media`  
> **Inference:** This succeeds because starting with `/` uses an absolute path from the root.

**Command: ls -l** **Resultant Directory Path:** `/media`  
> **Inference:** Shows visible files and directories in a detailed list format.

**Command: ls -al** **Resultant Directory Path:** `/media`  
> **Inference:** The `-a` flag shows hidden files (starting with a dot) along with detailed metadata.

---

## Part 2: File Operations and Cleanup

**Command: cd ~/ev4/4** **Command: mkdir emptydummy** **Command: mkdir dummy** **Command: cd dummy** **Command: touch file1** **Command: touch file2** **Command: ls -l** **Resultant Directory Path:** `/home/advait/ev4/4/dummy`  
> **Inference:** `touch` creates empty files. `ls -l` confirms `file1` and `file2` are created with zero-byte size.

**Command: rm -i file2** **Resultant Directory Path:** `/home/advait/ev4/4/dummy`  
> **Inference:** The `-i` flag prompts for confirmation before deleting as a safety measure.

**Command: ls -l** **Resultant Directory Path:** `/home/advait/ev4/4/dummy`  
> **Inference:** Confirms `file2` was removed successfully.

**Command: cd ..** **Command: rm emptydummy** **Resultant Directory Path:** `/home/advait/ev4/4`  
> **Inference:** This fails because `rm` is used for files; it cannot delete a directory without the `-r` flag.

**Command: rmdir emptydummy** **Resultant Directory Path:** `/home/advait/ev4/4`  
> **Inference:** This succeeds because `rmdir` is designed to remove directories that are completely empty.

**Command: rmdir dummy** **Resultant Directory Path:** `/home/advait/ev4/4`  
> **Inference:** This fails because `dummy` contains `file1`. `rmdir` only works on empty directories to prevent data loss.

**Command: rm -r dummy** **Resultant Directory Path:** `/home/advait/ev4/4`  
> **Inference:** This succeeds because the `-r` (recursive) flag forces the deletion of the directory and its contents.

---

## Part 3: Redirection and Content Manipulation

**Command: cat >file1.txt** **Command: cat >file2.txt** **Command: cat >file3.txt** > **Inference:** The `>` operator redirects output into a file, overwriting its contents.

**Command: cat file1.txt file2.txt > file_combined.txt** > **Inference:** Concatenates the first two files into a single new file.

**Command: cat file_combined.txt** > **Inference:** Using the Tab key while typing triggers autocomplete, completing the filename automatically.

**Command: cat file3.txt >> file_combined.txt** > **Inference:** The `>>` operator appends data to the end of the file instead of overwriting it.

**Command: grep -i hello file*** > **Inference:** Searches for the pattern "hello" case-insensitively in all files starting with "file".

**Command: cp file1.txt ~/ev4** > **Inference:** Copies the file to the parent folder; the original remains in the current directory.

**Command: mv file_combined.txt combined** > **Inference:** Moves the file to a new name within the same directory, acting as a rename.

---

## Part 4: Permissions and User Management

**Command: chmod u+x combined** > **Inference:** Grants execute permission to the user (owner).

**Command: chmod g-r combined** > **Inference:** Removes read permission from the group.

**Command: chmod 777 combined** > **Inference:** Assigns full permissions (Read=4, Write=2, Execute=1) to User, Group, and Others (4+2+1=7).

**Command: sudo useradd alice** > **Inference:** Creates a new user account named "alice".

**Command: sudo passwd alice** > **Inference:** Sets the password for user "alice".

**Command: sudo userdel alice** > **Inference:** Deletes the user account "alice".

---

## Part 5: Messaging and Communication

**Command: write [username]** > **Inference:** Allows sending real-time terminal messages to another logged-in user.

**Command: mesg y/n** > **Inference:** Toggles the ability to receive messages. `y` allows them, while `n` blocks them.

**Example Context:** User `advait` (Roll No: 4) can control his messaging status using these commands.
echo "'mesg y/n' - Enables or disables your terminal messaging visibility."

echo "Lab Script Execution Complete."
