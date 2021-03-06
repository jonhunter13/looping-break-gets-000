# Breaking and Gets

## What is the `break` keyword?

What happens when we have an infinite loop that keeps on going forever? What happens when, given a specific output, we want to break out of the loop? This is where the `break` keyword comes in.

Let's take a look at the following example:

```ruby
counter = 1

while counter <= 5
  puts "The counter is at: #{counter}"
  break if counter == 3
  counter = counter + 1
end

puts "We're done looping!"
```

We've added a `break` keyword in the `while` loop. When the condition `if counter == 3` is met, it will break out of the loop completely, and it will not continue to iterate all the way to 5. What's going to be the output?

```
"The counter is at: 1"
"The counter is at: 2"
"The counter is at: 3"
"We're done looping!"
```

## When to use `break`

Let's say we are writing a program in order to annoy someone (maybe a younger sibling or beloved coworker?) Our program should puts out the phrase "What's up, Doc?" again and again and again until our annoyed user finally inputs "STOP" into the terminal. In this case, we are looping indefinitely and breaking *if* a user inputs "STOP". 

Now that we've proposed a use case for the utilizing the `break` keyword, we're going to take a step back and discuss how to get and use a user's input. 

# Gets

The `gets` method accepts a single line of data from the standard input - the keyboard in this case. Then, your program can assign that value to a variable. 

*Not on standard input: The standard input is a default stream supplied by many operating systems that relates to the standard way to accept input from the user. In our case, the standard input is the keyboard. For now, just think of the standard input as what our user types into the terminal.*

We're going to play with method `greeting` that uses `puts` to ask a user for their name. Then, their response that they type into the terminal will be stored in a variable via the `gets` method. Then, the `greeting` method will proceed to puts out a greeting: "Your name is < name >"

Copy and paste the following into IRB: 

```ruby
def greeting
	puts "Please type your name:"
	name = gets
	puts "Your name is #{name}!"
end

greeting 
```

**A Note on `chomp`:** The `gets` method, used without `.chomp`, appends a new line to the data you are using it to "get". We don't want a new line! If we preserved our new line by failing to use `.chomp`, the final output of the `greeting` method would look like this: 

```ruby 
"Your name is <name>
!"
```

The `.chomp` method removes that new line for us. 

Now we'll return to our previous example using `break` and `gets`. 

## Our Annoying Program

Let's think about our example from earlier. We want a program that continuously outputs "Whats up, Doc?" until the user can't take it anymore and finally inputs "STOP". In other words, we need to create a *loop* that will continue to ask the user what's up, but *break* out of the loop when the user types in "STOP". 

This will require us to *get* some user input and break accordingly. 

Check out the following method:

```ruby
def annoying
	loop do 
		puts "What's up, Doc?"
		answer = gets.chomp
		break if answer == "STOP"
	end
	puts "Okay, okay, jeez. I'll stop. Sorry."
end

annoying
```

If you copy and paste the above code into IRB (hint: do it), you will probably be annoyed. Here's what happened when I copied and pasted the code into my terminal:

```ruby
What's up, Doc?
nothing
What's up, Doc?
I said nothing
What's up, Doc?
nothing!
What's up, Doc?
ugh
What's up, Doc?
quit it
What's up, Doc?
stop it
What's up, Doc?
stop
What's up, Doc?
stop
What's up, Doc?
STOP
Okay, okay, jeez. I'll stop. Sorry.
 => nil 
```

Let's break this down. We have a method, called `annoying`, that contains a loop. The loop says: 

* puts out a phrase, "What's up, Doc?"
* Collect the user's input via the `gets.chomp` methods and store them in a variable called `answer`. 
* Check to see if the `answer` variable points to a value of "STOP". 
* If it doesn't, go back to the top of the loop and repeat. If it does, `break` out of the loop and proceed to the next lines of code––"Okay, okay, jeez. I'll stop. Sorry."


# Using Gets and Break

## Instructions 

Fork and clone this lab. Read the below explanation and run the test suite to get started. 

* Okay, now that we've mastered feather levitation, we're ready for the levitation quiz! Fill out the content of the method `levitation_quiz` so that it contains a loop that asks the user "What is the spell that enacts levitation?" It should then store the answer in a variable called `answer` using the `gets.chomp` method. The loop should `break` if the user's answer is "Wingardium Leviosa". When the loop breaks, our method should puts out "You passed the quiz!" Otherwise, the loop should continue. 


