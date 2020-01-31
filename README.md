# NAME

Mojo::File::Role::Digest - A role for Mojo::File to calculate digests

# SYNOPSIS

    # single file
    use Mojo::File 'path';
    my $file = path($path)->with_roles('+Digest');

    # modified file class
    use Mojo::File;
    my $class = Mojo::File->with_roles('+Digest');
    my $file = $class->new($path);

    $file->md5_sum;
    $file->quickxor_hash;  # requires Digest::QuickXor
    $file->sha1_sum;
    $file->sha256_sum;

# DESCRIPTION

[Mojo::File::Role::Digest](https://metacpan.org/pod/Mojo%3A%3AFile%3A%3ARole%3A%3ADigest) is a role for [Mojo::File](https://metacpan.org/pod/Mojo%3A%3AFile) to calculate MD5, SHA1, SHA256, and QuickXor digests.

If the path isn't an existing file, all methods return an empty string `''`.

# APPLY ROLE

    use Mojo::File 'path';

    my $file             = path($path);
    my $file_with_digest = $file->with_roles('+Digest');

Apply to a single [Mojo::File](https://metacpan.org/pod/Mojo%3A%3AFile) object. See ["with\_roles" in Mojo::Base](https://metacpan.org/pod/Mojo%3A%3ABase#with_roles).

    use Mojo::File;
    my $class = Mojo::File->with_roles('+Digest');

    my $file1 = $class->new($path1);
    my $file2 = $class->new($path2);

Create a modified file class with applied digest role.

# METHODS

## md5\_sum

    $string = $file->md5_sum;

Returns the MD5 sum of the file in hexadecimal form. See ["hexdigest" in Digest::MD5](https://metacpan.org/pod/Digest%3A%3AMD5#hexdigest).

## quickxor\_hash

    $string = $file->quickxor_hash;

Returns the base64 encoded QuickXorHash of the file. See ["b64digest" in Digest::QuickXor](https://metacpan.org/pod/Digest%3A%3AQuickXor#b64digest).
Requires [Digest::QuickXor](https://metacpan.org/pod/Digest%3A%3AQuickXor) 0.03 or higher.

## sha1\_sum

    $string = $file->sha1_sum;

Returns the SHA1 sum of the file in hexadecimal form. See ["hexdigest" in Digest::SHA](https://metacpan.org/pod/Digest%3A%3ASHA#hexdigest).

## sha256\_sum

    $string = $file->sha256_sum;

Returns the SHA256 sum of the file in hexadecimal form. See ["hexdigest" in Digest::SHA](https://metacpan.org/pod/Digest%3A%3ASHA#hexdigest).

# AUTHOR & COPYRIGHT

© 2019–2020 by Tekki (Rolf Stöckli).

This program is free software, you can redistribute it and/or modify it under the terms of the Artistic License version 2.0.

# SEE ALSO

[Mojo::File](https://metacpan.org/pod/Mojo%3A%3AFile), [Mojo::Base](https://metacpan.org/pod/Mojo%3A%3ABase), [Role::Tiny](https://metacpan.org/pod/Role%3A%3ATiny), [Digest::MD5](https://metacpan.org/pod/Digest%3A%3AMD5), [Digest::QuickXor](https://metacpan.org/pod/Digest%3A%3AQuickXor), [Digest::SHA](https://metacpan.org/pod/Digest%3A%3ASHA).
