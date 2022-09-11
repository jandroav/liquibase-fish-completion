# :tropical_fish: liquibase-fish-completion :shell:

Liquibase shell completion for [fish shell](https://fishshell.com). Just place the `liquibase.fish` completion file under your user `.config/fish/completions/` folder and enjoy it!

Every command and argument is shown with its [official documentation](https://docs.liquibase.com/commands/home.html).

## :movie_camera: In action

[![Liquibase shell completion for fish shell](/img/youtube.png)](http://www.youtube.com/watch?v=Q-nYyONDv6Q "Liquibase shell completion for fish shell")

## :construction_worker: Contributions

Feel free to test this and propose changes or new commands by opening a [new pull request](https://github.com/jandroav/liquibase-fish-completion/pulls).

### :new: Adding new commands

1. Add the new command to the `liquibase_commands` list:

    ```
    set -l liquibase_commands init update update-sql update-count update-count-sql update-one-changeset update-one-changeset-sql update-testing-rollback update-to-tag update-to-tag-sql rollback rollback-sql rollback-to-date rollback-to-date-sql rollback-count rollback-count-sql \
    rollback-one-changeset rollback-one-changeset-sql rollback-one-update rollback-one-update-sql future-rollback-sql future-rollback-count-sql future-rollback-from-tag-sql generate-changelog snapshot snapshot-reference diff diff-changelog \
    history status calculate-checksum changelog-sync changelog-sync-sql changelog-sync-to-tag clear-checksums drop-all execute-sql list-locks mark-next-changeset-ran mark-next-changeset-ran-sql release-locks tag tag-exists unexpected-changesets validate \
    db-doc register-changelog sync-hub deactivate-changelog checks NEW_COMMAND
    ```

2. Make the new command available for completion:

    ```
    complete -f -c liquibase -n "not __fish_seen_subcommand_from $liquibase_commands" -a NEW_COMMAND -d 'Insert here its description'
    ```

3. Add its arguments:

    ```
    complete -f -c liquibase -n "__fish_seen_subcommand_from NEW_COMMAND; and not __fish_seen_subcommand_from --changelog-file" -a --changelog-file -d 'The root changelog'
    complete -f -c liquibase -n "__fish_seen_subcommand_from NEW_COMMAND; and not __fish_seen_subcommand_from --url" -a --url -d 'The JDBC database connection URL'
    complete -f -c liquibase -n "__fish_seen_subcommand_from NEW_COMMAND; and not __fish_seen_subcommand_from --username" -a --username -d 'The database username'
    complete -f -c liquibase -n "__fish_seen_subcommand_from NEW_COMMAND; and not __fish_seen_subcommand_from --password" -a --password -d 'The database password'
    ```