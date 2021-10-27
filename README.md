# Mobicint
Information Disclosure in Mobicint API for Credit Unions

## Summary:
Information regarding members is disclosed unnecessarily to an attacker. This information can be enumerated easily and provide an attacker partial email addresses as well as customer entered information. This can be combined with a member id number to lead to possible account compromise.
There is a possibility for further injection but I have not investigated due to lack of a security disclosure program or contact with the company.

## Steps To Reproduce:
Post data to the forgot password page in the memberID Field. The ID corresponds to the member number of actual credit union members.
![Posting Data](https://github.com/Laransec/Mobicint/blob/main/post_info.PNG)

Data is returned. The Label field is user generated and can contain sensitive information if the user has entered it. The address field is partially redacted.

![Returned Data](https://github.com/Laransec/Mobicint/blob/main/return_data_redacted.png)

## Possible Impacts:
Personal information can be compromised if the customer has entered it into the notes field. Further RCE may be possible as I was able to get a stack trace with some malformed input. I did not continue testing due to lack of documented security testing policies. 
