# Code of your exercise

Put here all the code created for this exercise

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
