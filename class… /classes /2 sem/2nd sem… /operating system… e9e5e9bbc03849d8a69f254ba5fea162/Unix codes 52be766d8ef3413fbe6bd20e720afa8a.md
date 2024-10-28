# Unix codes

```bash
# WAP to find combination of all the numbers that can be formed using 1,2,3

for ((i=1;i<=3; i++)); do
	for ((j=1;j<=3; j++)); do
		for ((k=1; k<=3; k++)); do
      	c="$i $j $k"
      	echo "$c"
    done
  done
done

```

```bash
# copy a file to another file
echo enter
read source target
if cp $source $target:
then
    echo "Copied file from '$source' to '$target'"
else
    echo "Could not copy file from '$source' to '$target'"
fi
```

```bash
# factorial
echo enter
read n
i=1
f=1
while [ $i -le $n ]
do
	f=$(($i*$f))
	i=$(($i+1))
done
echo $f

```

```bash
# fibonacii
echo enter
read n
x=0
y=1
echo  $x
echo  $y
for ((i=3; i<=n; i++))
do
    z=$((x + y))
    echo  $z
    x=$y
    y=$z
done

echo 

```

```bash
# loop
count=1
while [ $count -le 10 ]
do
	echo $count
	count=`expr $count + 1`
done

```

```bash
# prime
#!/bin/bash

read -p "Enter a number: " input

if [ $input -lt 2 ]; then
    echo "$input is not a prime number."
    exit
fi

for ((i=2; i<=input/2; i++)); do
    if [ $((input%i)) -eq 0 ]; then
        echo "$input is not a prime number."
        exit
    fi
done

echo "$input is a prime number."

```

```bash
# reverse

echo enter
read number
reversed_number=$(echo $number | rev)

echo "Original number: $number"
echo "Reversed number: $reversed_number"

```

```bash
# sum
echo heheh
read a
read b
echo $((a+b))
```

```bash
# until
i=1
until [ $i -gt 10 ]
do
	echo $i
	i=`expr $i + 1`
done

```

```bash
# matrix sum
#!/bin/bash

# Read the number of rows and columns
read -p "Enter the number of rows: " m
read -p "Enter the number of columns: " n

# Declare an array to store the matrix (initialize to 0 for clarity)
declare -A matrix

# Read matrix elements row-wise
for ((i=0; i<$m; i++)); do
  for ((j=0; j<$n; j++)); do
    read -p "Enter element [$i,$j]: " element
    matrix[$i,$j]=$element
  done
done
echo "The entered matrix is:"
for ((i=0; i<$m; i++)); do
  sum=0
  for ((j=0; j<$n; j++)); do
    sum=$((sum + ${matrix[$i,$j]}))
    printf "%d " "${matrix[$i,$j]}"
  done
  echo "$sum"
done
for((i=0;i<$n;i++)); do
  sum=0
  for((j=0;j<$m;j++)); do
    sum=$((sum + ${matrix[$j,$i]}))
  done
  echo -n "$sum "
done
echo
```

```bash

# positional parameters
# to be written on the command prompt not vi editor
set abhishek is genius
echo $1 $2 $3
set `cat abc`
echo $1 $2 $3
shift 2
echo $1 $2
echo $#
echo $*
```

```bash
# positional parameters
# copy file 1 content to file 2 and display the output
cp $1 $2
cat $2
```

```bash
# write a shell script which will recieve the file name during execution and
# disply file like ls -l
#!/bin/bash

# Prompt for filename
read -p "Enter a filename: " filename

# Check if the file exists
if [ ! -f "$filename" ]; then
  echo "Error: File '$filename' does not exist."
  exit 1
fi

# Get detailed file information using stat
file_info=$(stat -c "%a %n %U %G %s %x %b %y" "$filename")

# Extract and interpret permission information
permissions=${file_info:0:3}
owner=${file_info:4:8}
group=${file_info:13:8}
size=${file_info:22:8}
modified_time=$(date -d "@${file_info:31:12}")

# Get file type
file_type=$(stat -c "%F" "$filename")

# Print output in a similar format to ls -l
echo "File type:   $file_type"
echo "Permissions: $permissions"
echo "Owner:       $owner"
echo "Group:        $group"
echo "Size:        $size bytes"
echo "Last modified: $modified_time"

# Explain permission codes (optional)
echo "Permission explanation:"
echo "- (dash): Regular file"
echo "d (directory): Directory"
echo "l (symbolic link): Symbolic link"
echo "c (character device): Character device"
echo "b (block device): Block device"
echo "s (socket): Socket"
echo "r (read): Read permission"
echo "w (write): Write permission"
echo "x (execute): Execute permission"
echo "-" (hyphen): Permission not granted

# Note: The script provides an optional explanation of permission codes
# You can comment out the explanation section if desired.

```

```bash
# etc\password take login na ddisplay rest things basically use greg file
#!/bin/bash

# Check if a username is provided as an argument
if [ $# -eq 0 ]; then
  echo "Usage: $0 <username>"
  exit 1
fi

# Get the username from the first argument
username="$1"

# macOS uses dscl for user information management
user_info=$(dscl . -read /Users/$username)

# Check if the user exists
if [ -z "$user_info" ]; then
  echo "Error: User '$username' not found."
  exit 1
fi

# Extract relevant information from dscl output (adjust based on actual keys)
realname=$(echo "$user_info" | grep RealName | cut -d: -f2)
uid=$(echo "$user_info" | grep UniqueID | cut -d: -f2)
# Comment field might not be available in dscl output (check for its presence)
comment=$(echo "$user_info" | grep Comment | cut -d: -f2 || echo "N/A")  # Print N/A if not found
shell=$(echo "$user_info" | grep shell | cut -d: -f2)

# Display user information in a clear format
echo "Username: $username"
echo "Real Name: $realname"
echo "User ID (UID): $uid"
echo "Comment: $comment"
echo "Default Shell: $shell"
```

```bash
# ask name from user and display hello user
echo "What is your name ?"
read name
echo "Hello $name."

age=20
echo "$name is $age years old."

# =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
```

```bash
# mathematical operations
a=20 b=20

echo "There are two variables, "a" whose value is $a, and "b" whose value is $b."

echo "The sum of the two variables is: `expr $a + $b`"
echo "The difference between the two variables is: `expr $a - $b`"
echo "The product of the two variables is: `expr $a \* $b`"
echo "The quotient of the two variables is: `expr $a / $b`"
echo "The remainder of the two variables is: `expr $a % $b`"

echo "Task is complete."

# =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=

```

```bash
# mathematical operation of floating intergers
a=7.5 b=3.5

echo "There are two variables, "a" whose value is $a, and "b" whose value is $b."

echo "The sum of the two variables is: `expr "$a + $b" | bc`."
echo "The difference of the two variables is: `expr "$a - $b" | bc`."
echo "The product of the two variables is: `expr "$a * $b" | bc`."
echo "The quotient of the two variables is: `expr "$a / $b" | bc`."
echo "The remainder of the two variables is: `expr "$a % $b" | bc`."

echo "Task is complete."

# =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=

```

```bash
# numerical test
echo "This is a numerical test program."

echo -n "Enter any number: "
read num1
echo -n "Enter another number:"
read num2

echo "Following are the results after doing numerical test."

###

if [ $num1 -gt $num2 ]
then
	echo "[ -gt ]: $num1 is greater than $num2."
else
	echo "[ -gt ]: $num1 is less than $num2."
fi

###

if [ $num1 -lt $num2 ]
then
        echo "[ -lt ]: $num1 is less than $num2."
else
        echo "[ -lt ]: $num1 is greater than $num2."
fi

###

if [ $num1 -ge $num2 ]
then
        echo "[ -ge ]: $num1 is greater than or equal to $num2."
else        
	echo "[ -ge ]: $num1 is less than $num2."
fi

###

if [ $num1 -le $num2 ]
then
        echo "[ -le ]: $num1 is less than or equal to $num2."
else               
	echo "[ -le ]: $num1 is greater than $num2."
fi

###
          
if [ $num1 -ne $num2 ]
then         
	echo "[ -ne ]: $num1 is not equal to $num2."
else
        echo "[ -ne ]: $num1 is equal to $num2."
fi

###
   
if [ $num1 -eq $num2 ]
then          
	echo "[ -eq ]: $num1 is equal to $num2."
else
        echo "[ -eq ]: $num1 is not equal to $num2."
fi 

###

echo "Numerical Testing has been finished."

# =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=

```

```bash
# file test
echo "This is a file test program."

echo -n "Enter a directory/file name: "
read difi

echo "Following are the results after doing file test."

if [ -d "$difi" ]
then
	echo "[ -d ]: $difi exists and is a directory."
else
	echo "[ -d ]: $difi doesn't exist or is not a directory."
fi

###

if [ -f "$difi" ]
then
	echo "[ -f ]: $difi exists and is a regular file."
else
	echo "[ -f ]: $difi doesn't exist or is not a regular file."
fi

###

if [ -s "$difi" ]
then
        echo "[ -s ]: $difi exists and has a size greater than 0."
else
        echo "[ -s ]: $difi doesn't exist or doesn't has a size greater than 0."
fi 

###

if [ -r "$difi" ]
then
        echo "[ -r ]: $difi exists and read permission is granted."
else
        echo "[ -r ]: $difi doesn't exist or read permission is not granted."
fi

###

if [ -w "$difi" ]
then
        echo "[ -w ]: $difi exists and write permission is granted."
else
        echo "[ -w ]: $difi doesn't exist or write permission is not granted."
fi

### 
if [ -x "$difi" ]
then
	echo "[ -x ]: $difi exists and execute(or search) permission is granated."
else
	echo "[ -x ]: $difi doesn't exist or execute(or search) permission is not granted."
fi

###

echo "File Testing has been finished."

# =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=

```

```bash
# string test
echo "This is a String Test."

echo -n "Enter a string: "
read string_1
echo -n "Enter another string: "
read string_2

echo "Following are the results after doing the string test: "

if [ -n "$string_1" ]
then
	echo "[ -n ]-1: The length of ( $string_1 ) is nonzero."
else
	echo "[ -n ]-1: The length of ( $string_1 ) is zero."
fi

###

if [ -z "$string_2" ]
then
	echo "[ -z ]-2: The length of ( $string_2 ) is zero."
else
	echo "[ -z ]-2: The length of ( $string_2 ) is nonzero."
fi

###

if [ "$string_1" = "$string_2" ]
then
	echo "[ = ]: The two strings are equal."
else
	echo "[ = ]: The two strings are not equal."
fi

###

if [ "$string_1" != "$string_2" ]
then
	echo "[ != ]: The two strings are not equal."
else
	echo "[ != ]: The two strings are equal."
fi

###

echo "String testing has been finished."

# =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=

```

```bash

# case control
echo "This is a Case Control test. \n Enter any of the numbers in the range [12,8,10]"

echo -n "Enter a number: "
read num

case $num in
	12)
		echo "This is case 12."
		;;
	8)
		echo "This is case 8."
		;;
	10)
		echo "This is case 10."
		;;
	*)
		echo "This is default case."
		;;
esac

echo "Case Control Test is complete."

# =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=

```

```bash
# file which have read, write permission

echo "The files to which you have read, write and execute permissions are as follows: "

ls -l | grep "^-rwx"

echo "Finished."

```

```bash
# Write a shell script which will receive any number of filenames as arguments. The shell script should check whether every argument supplied is a file or a directory. If it is a directory it should be appropriately reported. If it is a filename then name of the file as well as the number of lines present in it should be reported.

echo "The results are: "

for item in "$@"
do
# if the item is a file
if [ ! -e "$item" ]
    then
        echo "$item does't exist"

    elif [ -f "$item" ]
        then
            num_lines=$(wc -l < "$item")
            echo "[ FILE ]: $item | [ LINES ]: $num_lines"

    elif [ -d "$item" ]
        then
            echo "[ DIRECTORY ]: $item"
    
    else
    echo "[ ERROR ]: Some error has occured."
fi
done
```

```bash
# The file /etc/passwd contains information about all the users. However it is difficult to decipher the information stored in it. Write a shell script which would receive the logname during execution, obtain information about it from /etc/passwd and display this information on the screen in easily understandable format.

echo "Following is the information of the passwd: "

grep ":" /etc/passwd | while IFS= read -r line

do

username=$(echo "$line" | cut -d: -f1)
uid=$(echo "$line" | cut -d: -f3)
gid=$(echo "$line" | cut -d: -f4)
home_directory=$(echo "$line" | cut -d: -f6)
shell=$(echo "$line" | cut -d: -f7)

    echo "[ Username ]: $username"
    echo "[ UID ]: $uid"
    echo "[ GID ]: $gid"
    echo "[ Home Directory ]: $home_directory"
    echo "[ Shell ]: $shell"
    echo "=-=-=-=-=-=-=-=-=-=-=-="

done
```

```bash
#  file counter
filecount=`ls | wc -l`

echo "There are currently $filecount files."

```

```bash
# Names of cities should be accepted from the keyboard. This list of cities should be combined with the list of cities present in the file cityfile. This combined list should be stored and the sorted output should be stored in a file newcity.

# Prompt the user to enter city names
echo "Enter city names (press Enter after each city, type 'done' when finished):"
cities=()
while true; do
    read city
    if [ "$city" = "done" ]; then
        break
    fi
    cities+=("$city")
done

# Write the given city names into "cityfile"
echo "${cities[@]}" >> cityfile

# Combine the user input with the cities from the file "cityfile"
combined_cities=("${cities[@]}")
while read -r city_from_file; do
    combined_cities+=("$city_from_file")
done < "cityfile"

# Sort the combined list of cities
sorted_cities=($(printf "%s\n" "${combined_cities[@]}" | sort))

# Write the sorted list to a new file named "newcity"
echo "${sorted_cities[@]}" > newcity

echo "Cities have been sorted and saved to 'newcity' file."

```

```bash
# All files present in a directory dir1 should be deleted. Any error, if it occurs while carrying out this operation should be stored in a file errorlog.

# Directory to delete files from
directory="dir1"

# Log file to store errors
error_log="errorlog"

# Delete files in the directory
rm -f "$directory"/* 2>> "$error_log"

# Check if any errors occurred
if [ $? -ne 0 ]; then
    echo "Errors occurred while deleting files in $directory. See $error_log for details."
fi
```

```bash
# Output of who should be displayed on the screen with value of total number of users who have logged in displayed at the bottom of the list

who

total_users=$(who | wc -l)
echo "Total number of users logged in: $total_users"
```

```bash
# Output of ls should be displayed on the screen and from this output the lines containing the word 'poem' should be counted and the count should be stored in a file file1.

ls_output=$(ls)

poem_count=$(echo "$ls_output" | grep -c 'poem')
echo "$poem_count" > file1
echo "$ls_output"
```

```bash
# Contents of file1 and file2 should be displayed on the screen and this output should be appended to the file file3

cat file1
cat file2

cat file1 file2 >> file3
```

```bash
# From output of ls the lines containing 'poem' should be displayed on the screen along with the count.

ls | grep 'poem' | tee /dev/tty | wc -l
```

```bash
# Output of who should be sorted and displayed on the screen along with the total number of users. The same output except the number of users should also be stored in a file file1.

sorted_output=$(who | sort)
num_users=$(who | wc -l)

# Display sorted output along with the total number of users
echo "Sorted Output of who:"
echo "$sorted_output"
echo "Total number of users: $num_users"

# Store the sorted output along with the total number of users in file1
echo "Sorted Output of who:" > file1
echo "$sorted_output" >> file1
echo "Total number of users: $num_users" >> file1
```

```bash
# Merge the contents of the files a.txt, b.txt and c.txt sort them and display the sorted output on the screen page by page

cat a.txt b.txt c.txt > merged.txt
sort merged.txt | more
rm merged.txt
```

```bash

```