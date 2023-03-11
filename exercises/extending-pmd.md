# Extending PMD

Use XPath to define a new rule for PMD to prevent complex code. The rule should detect the use of three or more nested `if` statements in Java programs so it can detect patterns like the following:

```Java
if (...) {
    ...
    if (...) {
        ...
        if (...) {
            ....
        }
    }

}
```
Notice that the nested `if`s may not be direct children of the outer `if`s. They may be written, for example, inside a `for` loop or any other statement.
Write below the XML definition of your rule.

You can find more information on extending PMD in the following link: https://pmd.github.io/latest/pmd_userdocs_extending_writing_rules_intro.html, as well as help for using `pmd-designer` [here](https://github.com/selabs-ur1/VV-ISTIC-TP2/blob/master/exercises/designer-help.md).

Use your rule with different projects and describe you findings below. See the [instructions](../sujet.md) for suggestions on the projects to use.

## Answer

We were not able to use PMD designer because of the javaFX version which was wrong, but we wrote a rule to find nested if statements:

```
<?xml version="1.0"?>

<ruleset name="Custom Rules">
    <description>
        Custom rules
    </description>
    <rule
    name="MandatoryBracesOnIf"
    language="java"
    message="detect the use of three or more nested if statements"
    class="net.sourceforge.pmd.lang.rule.XPathRule">
    <description>
        detect the use of three or more nested if statements
    </description>
    <priority>3</priority>
    <properties>
        <property name="xpath">
        <value><![CDATA[
            //IfStatement[descendant :: IfStatement[descendant :: IfStatement]]
        ]]></value>
        </property>
    </properties>
    </rule>
</ruleset>
```
I used the following command to look after 3 or more nested IF statements:
``./run.sh pmd -d /home/blanche/IdeaProjects/commons-collections/src -R /home/blanche/Documents/VV/rulesetcustomtest.xm``
, and PMD detected some in : commons-lang/src/test/java/org/apache/commons/lang3/SystemUtilsTest

also in commons-collections/src/main/java/org/apache/commons/collections4/trie/AbstractPatriciaTrie, here is the code example:

```
if (isValidUplink(node.parent.left, node.parent)) {
            if (node.parent.left == root) {
                if (root.isEmpty()) {
                    return null;
                }
                return root;

            }
            return node.parent.left;
        }
        return followRight(node.parent.left);
    }
