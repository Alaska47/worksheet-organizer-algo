## Usage
Read in the "worksheet" from a plaintext file (i.e `test.txt`)

```java
File file = new File("test.txt");
FileInputStream fis = new FileInputStream(file);
byte[] data = new byte[(int) file.length()];
fis.read(data);
fis.close();
String str = new String(data, "UTF-8");
```

Initialize a TagIdentifier object like this:

```java
TagIdentifier tg = new TagIdentifier(str /*string containing plaintext of worksheet*/, 5 /*number of tags you want to keep*/);
```

Generate and view tags like this:

```java
tg.generateTags();
System.out.println(Arrays.toString(tg.getTags()));
```

View identified subject like this:

```java
System.out.println(tg.getSubject());
```

In the *rare* case that the algorithm makes a mistake (picks the wrong subject), the algorithm can learn from its mistakes like this:

```java
/* Identifies selected tags as the indicated subject, and stores the data so it doesn't make the same mistake again */
tg.teachAlgo(subject /*the correct subject the tags should have identified as*/);
```

