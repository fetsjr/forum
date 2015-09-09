# Laravel 5.1 Forum Integration Package

## Installation

1.- Add to composer.json file the package
```
"socieboy/forum" : "dev-master"
```

2.- After installing this package, you have to set the service provider on your config/app.php file
```
Socieboy\Forum\Providers\ForumServiceProvider::class,
```

3.- Publish the forum config file on your config folder and publish the default template to your resources/assets/less/ folder, hit the follow command.
```
php artisan vendor:publish
```

4.- Create migrations for the forum, make sure you have a migration already created for users. Type the command:
```
php artisan forum:migrate
```
This command will create the migration files, for conversations, replies, and like_replies. Then just execute your migration:
```
php artisan migrate
```

## Configuration

### General

The forum provides a simple custom template, this is published on the resoruces/assets directory, feel free to edit.

On the config/forum.php file, set the right information of your app.

### Template

This is the master template view of your project:
```
    'template'  => 'app',
```

The key content is the name of your yield tag on your master template file where you would like to display the forum:
```
    'content'   => 'content',
```

With those values the forum can be adapted to your project really easily and match your application design.


### Topics or Categories

Define the array of topics for your forum.
Now you can define the key for the topic, give a name and the representative icon for the topic, you can use any font class of your preference here.
Also you can set the representative color for this topic in the las parameter.
```
    'topics' => [
        'general' => ['name' => 'General', 'icon' => 'fa fa-tags', 'color' => 'rgb(78, 137, 218)']
    ],
```

### User settings

The user configuration with the forum includes.

The model key, set the namespace + class name of your users model. By default is App\User as Laravel uses.
```
'model'         => \App\User::class,
```

The username key is the field on your users table that would be used to display the name of the user who post a conversation/reply. You can set any field like email, username, full_name, name, etc, (Must be a field on your users table).
```
    'username'    => 'name',
```

Do you have avatars for the users on your project. (Set the key avatar to true if you want to use avatars).
```
   'avatar'        => true,
```

Then define the field on your users table where the url to the image (avatar) is stored.
```
   'user-avatar'  => 'avatar',
```

If you want to include link to profile users, (When you hit the avatar or the name of other users display a user profile)
```
   'profile' => true,
```

By the fault the forum include a simple user profile. If you want to implement your own just set the route name on this key, just make sure that the route name recive the ID of the user.
```
'profile-route' => 'forum.user.profile'
```

Now if the user is not log in, the button for start a conversation will redirect the user to your login page, just set the url of your login page in this key. 
```
'auth' => [
    'login-url' => 'auth/login'
],
```

If you want you can change the icons to do like and choise the best answer on replies.
```
'icons' => [
    'like'              => 'glyphicon glyphicon-thumbs-up',
    'correct-answer'    => 'glyphicon glyphicon-ok',
],
```

### Emails

On the array emails are 4 different values.

The key fire is set by the default false, no email would be fired when someone left a reply. Change to true if you want to implement fire emails to the conversation owner when some user left a reply.
```
'fire' => false,
```

The from key is the email of the admin of your app or whatever account that wouldbe used to send the emails.
```
'from' => '',
```

The from-name key is the real name of the administrator of the forum or who is going to send the emails.
```
'from-name' => '',
```

Finally just set the subject for the emails fired.
```
'subject' => 'My app Forum - you have a new reply on your post',
```

Now that's it, easy and you are ready to go!

http://socieboy.com/forum
